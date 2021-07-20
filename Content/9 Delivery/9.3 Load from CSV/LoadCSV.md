# 🏗️ ПРОЦЕСС ЗАГРУЗКИ ДАННЫХ

  Каждый день _(В 07:15 загружаются DWH, в 22:00 - 1С)_ производится загрузка данных о клиентах банка. За каждый из запусков отвечает соответствующий таск, созданный в **`Task Scheduler`**

  ![img1](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/IMG/1.png?raw=true)

  Оба таска созданы под обычной базовой учеткой, **_НО_**  работают/запускаются из под системной учетки: **`EXPOMAIN\svc-ecc-CFTtoECC`**.

### Порядок загрузки:

  1. В заданное время срабатывает тригер, и таск запускает **PowerShell скрипт**.
  2. **PowerShell скрипт** отбирает соответствующий заданной маске архив с данными, распаковывает его в папку **`toLoad`** и производит загрузку данных в наши **_TMP таблицы_** путем вызова **`SQL*Loader`**.
  3. После того, как данные из файла были загружены в соответствующую таблицу, файл из **`toLoad`** перемещается в папку **`processed`**
  4. После загрузки всех файлов **PowerShell скрипт** запускает **`SQL*Plus`**, вызывающий пакет с процедурой загрузки.
  5. Процедура отбирает записи из **_TMP таблиц_** и производит **INSERT/UPDATE** записей в **_Eccentex таблицах_**
  6. После того как пункт 4 завершен, **PowerShell скрипт** отключается от БД ORACLE и очищает папку **`ToLoad`** от оставшихся файлов, если таковые имеются.
  7. Процесс загрузки завершен 👍

  **_NOTE:_** _Логи загрузки хранятся в папке с одноименным названием **`log`**_

### Мониторинг:

  * Понять какая из внутренних процедур пакета отработала _(при выполнение п.5)_ возможно, запустив **SQL** запрос:
```SQL
    --1C load time
    select * from TBL_ERRORS_LOAD_DWH where col_entity_id='-1' and col_error like '1C%' order by col_created desc;

    --DWH load time
    select * from TBL_ERRORS_LOAD_DWH where col_entity_id='-1' and col_error like 'DWH%' order by col_created desc;
```

 * Проверить были ли ошибки при загрузке воможно, запустив данный **SQL** запрос:
 ```SQL
    select * from TBL_ERRORS_LOAD_DWH where col_entity_id<>'-1' and col_error not like '%not found%' order by col_created desc
 ```