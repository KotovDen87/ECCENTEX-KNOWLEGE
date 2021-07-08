# НАСТРОЙКА СИСТЕМНЫХ ПЕРЕМЕННЫХ

1. Переходим в **`Setup`** солюшена
2. В сайдбаре **`Solution Preferences`** => **`System Variables`**
3. В открывшемся окне ищем и правим нужную нам переменную либо создаем новую

![img1](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/6%20Localization/IMG/1.png?raw=true)

4. В JS вызывается так:

```JavaScript
    Config.SYSTEM_VARIABLES.НАЗВАНИЕ_ПЕРЕМЕННОЙ
```


5. В SQL  вызывается так:

```SQL
    UPPER(GET_CONFIG('НАЗВАНИЕ_ПЕРЕМЕННОЙ'));
```



[back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/0%20Topics/README.md)