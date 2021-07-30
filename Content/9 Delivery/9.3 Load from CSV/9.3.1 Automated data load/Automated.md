# 🚅 ЕЖЕДНЕВНАЯ АВТОМАТИЧЕСКАЯ ЗАГРУЗКА ДАННЫХ

  Каждый день _(В 07:15 загружаются DWH, в 22:00 - 1С)_ автоматически производится загрузка данных о клиентах банка. За каждый из запусков отвечает соответствующий таск, созданный в **[`Task Scheduler`](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/9.3.3%20Task%20scheduler/TaskScheduler.md#-%D1%81%D0%BE%D0%B7%D0%B4%D0%B0%D0%BD%D0%B8%D0%B5-%D1%82%D0%B0%D1%81%D0%BA%D0%BE%D0%B2-%D0%B2-task-scheduler)**, который запускает **PowerShell скрипт** **`_LoadData.ps1`**.

  ![img1](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/9.3.1%20Automated%20data%20load/IMG/1.png?raw=true)

  Оба таска запускаются под системной учеткой: **`EXPOMAIN\svc-ecc-CFTtoECC`**.

### Порядок загрузки:

  1. Таск запускает **PowerShell скрипт**. Запуск происходит из каталога `..\\DWH` (_На ПРОД этот каталог находится на диске `E:\`)_.
  2. **PowerShell скрипт** отбирает соответствующий заданной маске _(текущая дата в названии архива)_ архив с данными, распаковывает его в папку **`toLoad`** и производит загрузку данных в наши **_TMP таблицы_** путем вызова **`SQL*Loader`**.
      * Для загрузки из **`CFT`**, архив берется из каталога `\\expobank.org\corp\Disk-W\EXPO-KRIF\arh`
      * Для загрузки из **`1С`**, архив берется из каталога `\\expobank.org\corp\Disk-W\EXPO-KRIF\arh_mkk`
      * **_TMP таблицы_** - это таблицы, созданные в БД на каждый файл в архиве. Название таблицы соответствует названию файла
      **_Пример:_** _В архиве существует файл, `DWH_PROPERTY_VALUE_CFT_20210720192125.csv`, соответственно загрузка будет осуществлятся в таблицу `DWH_PROPERTY_VALUE_CFT`, аналогично для остальных файлов._
      * По составу полей **_TMP таблицы_** повторяют структуру загружаемого в нее файла **`*.CSV`** из архива.
  3. После того, как данные из файла были загружены в соответствующую таблицу, файл из **`toLoad`** перемещается в папку **`processed`**
  4. После загрузки всех файлов **PowerShell скрипт** запускает **`SQL*Plus`**, вызывающий БД пакет с процедурой загрузки.
      * При загрузке из **`CFT`** вызывается процедура пакета **`LOAD_DATA_FROM_DWH.LoadDwhData()`**
      * При загрузке из **`1C`** вызывается процедура пакета **`LOAD_DATA_FROM_DWH.Load1CData()`**
  5. Процедура отбирает записи из **_TMP таблиц_** и производит **INSERT/UPDATE** записей в **_Eccentex таблицах_**
  6. После того как _п.4_ завершен, **PowerShell скрипт** отключается от БД ORACLE и очищает папку **`ToLoad`** от оставшихся файлов, если таковые имеются.
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

  * Посмотреть все ли записи загружены в **TMP таблицы** можно, запустив один из запросов:
```SQL
  select count(1) from DWH_PERSON_CFT where col_status='NEW';
  select count(1) from DWH_PHONE_CFT where col_status='NEW';
  select count(1) from DWH_ADDRESS_CFT where col_status='NEW';
  select count(1) from DWH_DEBT_STATIC_CFT where col_status='NEW';
  select count(1) from DWH_DEBT_CFT where col_status='NEW';
  select count(1) from DWH_ACCOUNT_DEBT_CFT where col_status='NEW';
  select count(1) from DWH_ACCOUNT_REST_CFT where col_status='NEW';
  select count(1) from DWH_DEBT_STRUCTURE_CFT where col_status='NEW';
  select count(1) from DWH_INTEREST_RATE_CFT where col_status='NEW';
  select count(1) from DWH_GUARANTEE_CFT where col_status='NEW';
  select count(1) from DWH_PROPERTY_CFT where col_status='NEW';
  select count(1) from DWH_PROPERTY_VALUE_CFT where col_status='NEW';
  select count(1) from DWH_PROPERTY_PARAM_CFT where col_status='NEW';
  select count(1) from DWH_DEBT_PAYMENTS_CFT where col_status='NEW';
```


<br/>

[go back](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/LoadCSV.md#%EF%B8%8F-%D0%BF%D1%80%D0%BE%D1%86%D0%B5%D1%81%D1%81-%D0%B7%D0%B0%D0%B3%D1%80%D1%83%D0%B7%D0%BA%D0%B8-%D0%B4%D0%B0%D0%BD%D0%BD%D1%8B%D1%85) | [back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/0%20Topics/Topics.md#-topics)