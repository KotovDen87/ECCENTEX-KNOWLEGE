# 💩 ЗАГРУЗКА ТЕСТОВЫХ ДАННЫХ

### ОБНОВЛЕНИЕ ДАННЫХ НА `QA`

<details><summary><i><h7>click to expand!</h7></i></summary>

1. Открываем **PowerShell 7.1** _(желательно от админа)_

![img1](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/9.3.4%20Data%20for%20testing/IMG/1.png?raw=true)

2. Переходим в каталог с скриптом `E:\DWH`
```PowerShell
    > cd E:\DWH
    # или
    > Set-Location E:\DWH
```

3. Запускаем скрипт `LoadData_QA.ps1` с нужным параметром
```PowerShell
    #FOR 1C archive
    > ./LoadData_QA.ps1 '1C'

    #FOR DWH archive
    > ./LoadData_QA.ps1 'DWH'
```
**_NOTE:_** _Для загрузки архива за конкретную дату, необходимо открыть скрипт в редакторе и в соответствующей строке задать маску:
  * `49` при загрузке **DWH**
  * `219` при загрузке **1C**
```PowerShell
    # DEFAULT
    $SearchMask = Get-Date -Format "yyyyMMdd"

    # U can write date whatever u want for tests
    $SearchMask = "20210729"
```

4. Ждем заверщения 😉

![img2](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/9.3.4%20Data%20for%20testing/IMG/2.png?raw=true)

</details>

### ЗАГРУЗКА ДАННЫХ В ТМП-таблицы

<details><summary><i><h7>click to expand!</h7></i></summary>


</details>


<br/>

[go back](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/LoadCSV.md) | [back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/0%20Topics/Topics.md)