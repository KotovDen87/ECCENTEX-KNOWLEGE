# ⚙️ СИСТЕМНЫЕ ПЕРЕМЕННЫЕ

1. Переходим в **`Студия приложений`** и выбираем нужный **SOLUTION**

![AppStudio](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/IMG/AppStudio.png?raw=true)

2. В сайдбаре **`Solution Preferences`** => **`System Variables`** _(для DEV)_ либо **`Environment Variables`** _(для PROD и QA)_

3. В открывшемся окне ищем и правим нужную нам переменную либо создаем новую

![img1](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/7%20System%20Variables/IMG/1.png?raw=true)


**_NOTE:_** _Каждая среда имеет свои конкретные настройки. После создания/редактирования на DEV необходимо проделать те же операции на QA и PROD (после успешного тестирования) средах_

Вызов переменных:
* В **JavaScript** вызывается следующим образом:

```JavaScript
    Config.SYSTEM_VARIABLES.НАЗВАНИЕ_ПЕРЕМЕННОЙ
```

* В **SQL** вызывается следующим образом:

```SQL
    UPPER(GET_CONFIG('НАЗВАНИЕ_ПЕРЕМЕННОЙ'));
```


<br/>

[back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/0%20Topics/Topics.md)