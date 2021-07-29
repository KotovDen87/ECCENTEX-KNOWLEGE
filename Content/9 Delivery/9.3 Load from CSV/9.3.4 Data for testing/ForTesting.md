# 💩 ЗАГРУЗКА ТЕСТОВЫХ ДАННЫХ

### ОБНОВЛЕНИЕ ДАННЫХ НА `QA`

<details><summary><i><h7>click to expand!</h7></i></summary>

1. Открываем **PowerShell 7.1** _(желательно от админа)_

![img1](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/9.3.4%20Data%20for%20testing/IMG/1.png?raw=true)

2. Переходим в каталог с скриптом `E:\DWH`
```PowerShell
    > cd E:\DWH
```

3. Запускаем скрипт `LoadData_QA.ps1` с нужным параметром
```PowerShell
    # For the 1C archive
    > ./LoadData_QA.ps1 '1C'

    # For the DWH archive
    > ./LoadData_QA.ps1 'DWH'
```
**_NOTE:_** _Для загрузки архива за конкретную дату, необходимо открыть скрипт в редакторе и в соответствующей строке задать маску:
  * `49` при загрузке **DWH**
  * `219` при загрузке **1C**
```PowerShell
    # DEFAULT
    $SearchMask = Get-Date -Format "yyyyMMdd"

    # Format must be: yyyyMMdd
    $SearchMask = "20210729"
```

4. Ждем заверщения 😉

![img2](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/9.3.4%20Data%20for%20testing/IMG/2.png?raw=true)

</details>

### ЗАГРУЗКА ДАННЫХ В ТМП-таблицы

<details><summary><i><h7>click to expand!</h7></i></summary>

1. Разархивируем архив в папку **`E:\DWH\`** **`toLoad`**
2. Запускаем скрипт `TMP_only.ps1` одним из способов:
    * Через консоль **PowerShell**
    * Руками: кликаем **ПКМ** по файлу => `run with PowerShell`

**_NOTE:_**
1. По дефолту в скрипте заданы логин/пароль **PROD** среды. _(QA данные закомментированы)_
2. Список файлов для загрузки указан на `22` строке. _(Вы можете закомментировать не нужные, при загрузке)_
3. Если запус скрипта производится не от **Админа**:
    * Логи на строках: `61` `62` `63` `65`, нужно закомментировать
    * Строки: `17` и `67`, нужно закомментировать

</details>


<br/>

[go back](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/LoadCSV.md) | [back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/0%20Topics/Topics.md)