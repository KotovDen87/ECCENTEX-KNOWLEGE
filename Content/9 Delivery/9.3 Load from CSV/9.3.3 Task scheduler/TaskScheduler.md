# 🕑 СОЗДАНИЕ ТАСКОВ В TASK SCHEDULER

1. Открываем **`Task Scheduler`** _(Планировщик задач)_ => Переходим в **`Task Scheduller Library`** => В основном окне кликаем **ПКМ** **`Create New Task...`**

![img1](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/9.3.3%20Task%20scheduler/IMG/1.png?raw=true)

2. В открывшемся окне, вкладка `General`, заполняем:
    * `Name`
    * `Description` _(optional)_,
    * Выбираем юзера под которым таск будет запускаться, кнопка `Change User or Group...`
    * Выбираем `Run whether user is logged on or not`
    * Ставим галку `Run with highest privileges`

**_NOTE:_** _Если не менять юзера, таск запустится под юзером, создавшим таск_

![img2](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/9.3.3%20Task%20scheduler/IMG/2.png?raw=true)

3. На вкладке `Triggers` кликаем `NEW...` и заполняем информацию о том, когда таск должен запускаться

![img3](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/9.3.3%20Task%20scheduler/IMG/3.png?raw=true)

4. На вкладке `Actions` выбираем программу, которая будет стартовать. В данном случае это `C:\Program Files\PowerShell\7\pwsh.exe` с аргументами:
    * `-executionPolicy bypass -Command "& 'E:\DWH\procedures\_LoadData.ps1' '1C'"` для старта функции загрузки **1С**-архива
    * `-executionPolicy bypass -Command "& 'E:\DWH\procedures\_LoadData.ps1' 'DWH'"` для старта функции загрузки **DWH**-архива

**_NOTE:_** _При выборе программы, прописан полный путь до обновленной версии **`PowerShell 7.1`**. Если будет напишсано `PowerShell`, то запустится стандартная версия `5.1` (дефолтная версия для **Win 10**)_

![img4](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/9.3.3%20Task%20scheduler/IMG/4.png?raw=true)

5. На вкладке `Conditions` оставляем все как на рисунке ниже

![img5](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/9.3.3%20Task%20scheduler/IMG/5.png?raw=true)

6. На вкладке `Settings` оставляем все как на рисунке ниже

![img6](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/9.3.3%20Task%20scheduler/IMG/6.png?raw=true)

7. Сохраняем таск и после сохранения, кликаем **ПКМ** по таску и жмем `Export`. Сохраняем в удобное для вас место.

8. Открываем полученную **XML** в любом редакторе и в теге `Priority` _(line 43)_ меняем значение на **`4`**. Сохраняем.
```XML
  <Priority>4</Priority>
```
  * Примеры актуальных XML:
    * для **[`DWH`](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/9.3.3%20Task%20scheduler/XML/EXP%20DWH%20Import%20PS.xml)**
    * для **[`1C`](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/9.3.3%20Task%20scheduler/XML/EXP%201C%20Import%20PS.xml)**
9. Импортируем обновленный таск в **`Task Scheduler`**, удалив при этом старую версию.


<br/>

[go back](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/9%20Delivery/9.3%20Load%20from%20CSV/LoadCSV.md#%EF%B8%8F-%D0%BF%D1%80%D0%BE%D1%86%D0%B5%D1%81%D1%81-%D0%B7%D0%B0%D0%B3%D1%80%D1%83%D0%B7%D0%BA%D0%B8-%D0%B4%D0%B0%D0%BD%D0%BD%D1%8B%D1%85) | [back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/0%20Topics/Topics.md)