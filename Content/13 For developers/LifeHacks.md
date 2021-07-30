# 🙏 ДЛЯ РАЗРАБОТЧИКОВ _(наблюдения и полезности)_

### НАБЛЮДЕНИЯ ПО ExtJS

1. Почему именно 5.1 версия, а не более новые?
  - Из-за **совместимости**. На данный момент это самая стабильно работающая с **Eccentex** версия

1. Где можно посмотреть все уже созданные компоненты **`xtype`** _(компонет, который мы можем юзать в разных частях)_
  - Файл **DCM_GLOBAL_JS.js** объект **`SDCommon`**, НО в большинстве случаев используются стандартные.

1. Где посмотреть возможные свойства у **`xtype`**, в [официальной документации](https://docs.sencha.com/extjs/5.1.1/index.html) обычно только описание элемента, а о его свойствах ничего
  - Можно через консоль браузера вывести и посмотреть

1. Иконку для кнопок можно вставить таким образом, а как посмотреть список возможных вариантов?
```JavaScript
iconCls: EcxUtils5.Awesome.icon('download')
```
  - Можно через консоль браузера вывести и посмотреть

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
    --WHERE (NLS_LOWER(t.PROGRAM) = 'cash.exe') -- посмотреть сессии от программы cash.exe
    --WHERE status='ACTIVE' and osuser!='SYSTEM' -- посмотреть пользовательские сессии
    --WHERE username = 'схема' -- посмотреть сессии к схеме (пользователь)
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