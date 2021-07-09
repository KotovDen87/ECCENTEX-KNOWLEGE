# СИСТЕМНЫЕ ПЕРЕМЕННЫЕ

1. Переходим в **`Студия приложений`** и выбираем нужный **SOLUTION**

![img1](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/IMG/AppStudio.png?raw=true)

2. В сайдбаре **`Solution Preferences`** => **`System Variables`**
3. В открывшемся окне ищем и правим нужную нам переменную либо создаем новую

![img1](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/7%20System%20Variables/IMG/1.png?raw=true)

4. Созданная переменная в **JavaScript** вызывается следующим образом:

```JavaScript
    Config.SYSTEM_VARIABLES.НАЗВАНИЕ_ПЕРЕМЕННОЙ
```


5. Созданная переменная в **SQL** вызывается следующим образом:

```SQL
    UPPER(GET_CONFIG('НАЗВАНИЕ_ПЕРЕМЕННОЙ'));
```


<br/>

[back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/0%20Topics/README.md)