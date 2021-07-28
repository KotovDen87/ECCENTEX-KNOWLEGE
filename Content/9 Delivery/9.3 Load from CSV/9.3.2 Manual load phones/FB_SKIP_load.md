# 📲 ЗАГРУЗКА ДОП. ТЕЛЕФОНОВ

На данный момент **`загрузка дополнительных телефонов`** _(Обогащение)_ производится в ручном режиме. Для этого создан отдельный скрипт, написанный на **PowerShell**.

Процесс загрузки простой, но время затратный:

1. Первое что необходимо сделать, проверить сам файл на соответствие заданному формату:
`client_id`, `phone_id`, `phone_num`, `typ`, `contact_face`, `active`, `dsc`

![Columns Format](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/9.3.2%20Manual%20load%20phones/IMG/1.png?raw=true)

**_NOTE:_** _Важно поставить "**пробел**" в колонке **`H`**. Иначе **`SQL*Loader`** не распознает начало новой строки._

2. Проверяем поле **`client_id`** на корректность данных, т.к. встречаются данные со значением вида: **`1.03546E+11`**.
Исправить это не сложно:
  1. Задайте формат ячейки: `Дополнительный`
  1. Тип: `Zip Code`


```PowerShell
    #   Setup parameters
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
<br/>

[go back](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/LoadCSV.md) | [back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/0%20Topics/Topics.md)