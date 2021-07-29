<!-- ЛОКАЛЬНО ЗАПУСТИТЬ ДЕВ СРЕДУ -->

node .\node_modules\pm2\bin\pm2 start server.js
node .\node_modules\pm2\bin\pm2 stop server.js

запуск локально:
  в консоли браузера вписать:
    document.cookie = 'ConfigDevUrl=http://localhost:1841/config/ecx/config-dev-nores.js'

<!-- СБОР СТАТИСТИКИ в БД -->
  DBMS_STATS.GATHER_TABLE_STATS('ЮЗЕР', 'ТАБЛИЦА');


<!-- СЕССИИ БД -->
--смотрим сессии

  SELECT t.SID, t.SERIAL#, t.osuser as "User", t.MACHINE as "PC", t.PROGRAM as "Program"
  FROM v$session t
  --WHERE (NLS_LOWER(t.PROGRAM) = 'cash.exe') -- посмотреть сессии от программы cash.exe
  --WHERE status='ACTIVE' and osuser!='SYSTEM' -- посмотреть пользовательские сессии
  --WHERE username = 'схема' -- посмотреть сессии к схеме (пользователь)
  ORDER BY 4 ASC;

  --убиваем сессии (вставить сид и серию)
  begin
  sys.kill_session(sid,serial)
  end

<!--   РЕБИЛД ИНДЕКСОВ  -->

SELECT 'ALTER INDEX ' || OWNER || '.' ||
INDEX_NAME || ' REBUILD ' ||
' TABLESPACE ' || TABLESPACE_NAME || ';'
FROM DBA_INDEXES
WHERE STATUS='UNUSABLE'
UNION
SELECT 'ALTER INDEX ' || INDEX_OWNER || '.' ||
INDEX_NAME ||
' REBUILD PARTITION ' || PARTITION_NAME ||
' TABLESPACE ' || TABLESPACE_NAME || ';'
FROM DBA_IND_PARTITIONS
WHERE STATUS='UNUSABLE'
UNION
SELECT 'ALTER INDEX ' || INDEX_OWNER || '.' ||
INDEX_NAME ||
' REBUILD SUBPARTITION '||SUBPARTITION_NAME||
' TABLESPACE ' || TABLESPACE_NAME || ';'
FROM DBA_IND_SUBPARTITIONS
WHERE STATUS='UNUSABLE';