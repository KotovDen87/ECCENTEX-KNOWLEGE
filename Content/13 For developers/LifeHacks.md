# 🙏 ДЛЯ РАЗРАБОТЧИКОВ _(наблюдения и полезности)_

### НАБЛЮДЕНИЯ ПО ExtJS

1. Почему именно 5.1 версия, а не более новые?
    * Из-за **СОВМЕСТИМОСТИ**. На данный момент это самая стабильно работающая с **Eccentex** версия

1. Где можно посмотреть все уже созданные компоненты **`xtype`** _(компонет, который мы можем юзать в разных частях)_
    * Файл **DCM_GLOBAL_JS.js** объект **`SDCommon`**, НО в большинстве случаев используются стандартные.

1. Где посмотреть возможные свойства у **`xtype`**, в [официальной документации](https://docs.sencha.com/extjs/5.1.1/index.html) обычно только описание элемента, о свойствах ничего
    * Можно через консоль браузера вывести и посмотреть

1. Иконку для кнопок можно вставить таким образом _(см. ниже)_, а как посмотреть список возможных вариантов?
    * Можно через консоль браузера вывести и посмотреть
```JavaScript
  iconCls: EcxUtils5.Awesome.icon('download')
```


### ЛОКАЛЬНЫЙ ЗАПУСК DEV-среды

1. В **консоле** запускаем сервер:
```PowerShell
  # For START server
  > node .\node_modules\pm2\bin\pm2 start server.js

  # For STOP server
  > node .\node_modules\pm2\bin\pm2 stop server.js
```
2. В **консоле** браузера _(вызывается на `F12`)_ вписать:
```JavaScript
  document.cookie = 'ConfigDevUrl=http://localhost:1841/config/ecx/config-dev-nores.js'
```

### СБОР СТАТИСТИКИ в БД
```SQL
  DBMS_STATS.GATHER_TABLE_STATS('USER_NAME', 'TABLE_NAME');
```
### NLS ПАРАМЕТРЫ БД
```SQL
  SELECT * FROM nls_session_parameters;
```
### МОНИТОРИНГ СЕССИЙ БД

```SQL
  -- Мониторинг сессий
  SELECT t.SID, t.SERIAL#, t.osuser as "User", t.MACHINE as "PC", t.PROGRAM as "Program"
  FROM v$session t
  -- WHERE (NLS_LOWER(t.PROGRAM) = 'cash.exe') -- посмотреть сессии от программы cash.exe
  -- WHERE status='ACTIVE' and osuser!='SYSTEM' -- посмотреть пользовательские сессии
  -- WHERE username = 'схема' -- посмотреть сессии к схеме (пользователь)
  ORDER BY 4 ASC;

  -- Убиваем сессии (вставить sid и serial)
  BEGIN sys.kill_session(sid,serial) END;
```

### РЕБИЛД ИНДЕКСОВ
```SQL
  SELECT 'ALTER INDEX ' || OWNER || '.' || INDEX_NAME || ' REBUILD ' || ' TABLESPACE ' || TABLESPACE_NAME || ';'
  FROM DBA_INDEXES WHERE STATUS='UNUSABLE'
  UNION
  SELECT 'ALTER INDEX ' || INDEX_OWNER || '.' || INDEX_NAME || ' REBUILD PARTITION ' || PARTITION_NAME || ' TABLESPACE ' || TABLESPACE_NAME || ';'
  FROM DBA_IND_PARTITIONS WHERE STATUS='UNUSABLE'
  UNION
  SELECT 'ALTER INDEX ' || INDEX_OWNER || '.' || INDEX_NAME || ' REBUILD SUBPARTITION '||SUBPARTITION_NAME|| ' TABLESPACE ' || TABLESPACE_NAME || ';'
  FROM DBA_IND_SUBPARTITIONS WHERE STATUS='UNUSABLE';
```

### ПРОВЕРКА ЗАПРОСА НА БЫСТРОДЕЙСТВИЕ
```SQL
  -- STEP 1: run ALTER
  ALTER SESSION SET SQL_TRACE=TRUE

  -- STEP 2: copy/paste SQL & run request
  SELECT COL_ID, col_sd_individexternalparty FROM TBL_SD_INDIVIDUALS WHERE COL_PERSONID = '92547876652';


  -- STEP 3: find ID your SQL request
  SELECT sql_id, sql_text FROM v$sql WHERE MODULE = 'SQL Developer' ORDER BY last_active_time DESC;
  SELECT sql_id, sql_text FROM v$sql WHERE MODULE = 'SQL Developer' ORDER BY last_load_time DESC;


  -- STEP 4: run it with ID
  DECLARE
    l_sql_tune_task_id  VARCHAR2(100);
  BEGIN
    l_sql_tune_task_id := DBMS_SQLTUNE.create_tuning_task (
                            sql_id      => '&SQL_ID',
                            scope       => DBMS_SQLTUNE.scope_comprehensive,
                            time_limit  => 1000,
                            task_name   => '&SQL_ID',
                            description => 'Tuning task for statement ' || '&SQL_ID');
  END;
  /

  -- STEP 5: run it with ID
  CALL DBMS_SQLTUNE.execute_tuning_task('&SQL_ID');
  -- STEP 6: run it (optional)
  SELECT task_name, status FROM dba_advisor_log WHERE owner = 'ENVIRONMENT';

  -- STEP 7: run it with ID to see recommendations
  SELECT DBMS_SQLTUNE.report_tuning_task('&SQL_D') AS recommendations FROM dual;

  -- To apply start new command window and make sure that user has
  --   administer sql tuning set
  --   advisor
  --   alter any sql profile
  --   create any sql profile
  -- system privileges

  -- reset the previous task
  -- BEGIN
  -- 	DBMS_SQLTUNE.drop_tuning_task(task_name => '17puxwbgy0g14');
  -- END;

  -- ALTER SESSION SET SQL_TRACE=TRUE
  -- SELECT * FROM v$sql
  -- SELECT task_name, status FROM dba_advisor_log
  -- DBMS_SQLTUNE
```