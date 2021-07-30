# 📲 ЗАГРУЗКА ДОП. ТЕЛЕФОНОВ

На данный момент **`загрузка дополнительных телефонов`** _(Обогащение)_ производится в ручном режиме. Для этого создан отдельный скрипт, написанный на **PowerShell**.
<details><summary><i><h7>click to see script!</h7></i></summary>

```PowerShell
  # Setup parameters
  $env:NLS_LANG = "RUSSIAN_RUSSIA.CL8MSWIN1251"
  CHCP 1251

  # $USERNAME = USERNAME=ENV_QA
  # $USERNAME = PWD=ENV_QA6
  $USERNAME = "ENVIRONMENT"
  $PSWRD = "ENVIRONMENT3"
  $TNS = "EXPO"

  # Path to the dir with script file
  $ScriptFolder = "E:\DWH"
  $ToLoad = "$ScriptFolder\toLoad"
  $Log = "$ScriptFolder\log"

  # Start load data
  # loads phones into DWH_PHONE_CFT fabrica
  &sqlldr "$USERNAME/$PSWRD@$TNS" DATA="$toLoad\FB_PHONE.csv" LOG="$Log\FB_PHONE.log" BAD="$ScriptFolder\FB_PHONE.bad" CONTROL="$ScriptFolder\ctrlfiles\PHONE\ctrl_FAB_DWH_PHONE_CFT.ctl"
  # loads phones into DWH_PHONE_CFT skip
  &sqlldr "$USERNAME/$PSWRD@$TNS" DATA="$toLoad\SK_PHONE.csv" LOG="$Log\SK_PHONE.log" BAD="$ScriptFolder\SK_PHONE.bad" CONTROL="$ScriptFolder\ctrlfiles\PHONE\ctrl_SKIP_DWH_PHONE_CFT.ctl"

  exit
```

</details>

Процесс загрузки простой, но время затратный:

1. Первое что необходимо сделать, проверить сам файл на соответствие заданному формату:

`client_id`, `phone_id`, `phone_num`, `typ`, `contact_face`, `active`, `dsc`

![Columns Format](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/9.3.2%20Manual%20load%20phones/IMG/1.png?raw=true)

**_NOTE:_** _Важно поставить "**пробел**" в колонке **`H`**. Иначе **`SQL*Loader`** не распознает начало новой строки._

2. Проверяем поле **`client_id`** на корректность данных, т.к. встречаются данные со значением вида: **`1.03546E+11`**. Исправить это не сложно:
    * Задайте формат ячейки: `Дополнительный`
    * Тип: `Zip Code`
3. Сохраняем файл Следующим образом:
    * Имя файла: `FB_PHONE` - для источника **Фабрика**; `SK_PHONE` - для источника **Скип** _(мобильный розыск)_
    * Тип файла: `CSV (разделители - запятые)(*.csv)`

![Save file](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/9.3.2%20Manual%20load%20phones/IMG/2.png?raw=true)

4. Проверяем файл в **`Notepad++`**. Если "**пробел**" был проставлен, то последний символ строки будет **`,`** _(см. рисунок ниже)_

![Right File](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/9.3.2%20Manual%20load%20phones/IMG/3.png?raw=true)

5. Переходим на удаленку в папку **`E:\DWH\`** => загружаем полученный файл в **`toLoad`**
6. Кликаем **ПКМ** по файлу **`FB_SKIP_only.ps1`** => `run with PowerShell`
7. После загрузки данных в ТМП-таблицу **DWH_PHONE_CFT** заходим в БД:
  * Смотрим все ли записи загружены
```SQL
  SELECT count(1) FROM DWH_PHONE_CFT WHERE col_status='NEW';
```

  * Запускаем процедуру
```SQL
  DECLARE
    sErrorMessage VARCHAR(2000);
  BEGIN
    LOAD_DATA_FROM_DWH.LoadPhones('FULL_LOAD', sErrorMessage);
  END;
```

  * Запускаем SQL-запросы, для проверки. _(Если **все** данные успешно загружены COUNT = 0. Если нет, разбираемся почему не загружены)_
```SQL
  SELECT count(1) FROM DWH_PHONE_CFT WHERE col_status='NEW';
  SELECT count(1) FROM DWH_PHONE_CFT WHERE col_status='ERROR';
```


<br/>

[go back](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/LoadCSV.md#%EF%B8%8F-%D0%BF%D1%80%D0%BE%D1%86%D0%B5%D1%81%D1%81-%D0%B7%D0%B0%D0%B3%D1%80%D1%83%D0%B7%D0%BA%D0%B8-%D0%B4%D0%B0%D0%BD%D0%BD%D1%8B%D1%85) | [back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/0%20Topics/Topics.md)