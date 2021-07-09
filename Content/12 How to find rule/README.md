# ПОИСК ФАЙЛА ДЛЯ ПРАВОК

1. Переходим в **`Setup`** солюшена

![SolutionSetup](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/IMG/SolutionSetup.png?raw=true)

2. В сайдбаре **`Forms and Pages`** => **`Detail Pages`** => Кликаем по нужной форме

![img1](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/12%20How%20to%20find%20rule/IMG/1.png?raw=true)

3. В открывшемся окне видно название для **`Coded Page`**
4. Копируем название и переходим в пункт меню **`Coded Page`**
5. Ищем нужную нам запись и кликаем **`EDIT`** _(Редактировать)_
6. В открывшемся окне видим путь до нужного нам файла/папки

![img2](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/12%20How%20to%20find%20rule/IMG/2.png?raw=true)


<br/>

Что делать если нам необходимо исправить рул главной формы, на которой у нас располагались все вкладки? Для этого:

1. Переходим в раздел **`External Parties`** => **`External Party Types`**
2. Кликаем на нужную форму _(в нашем случае **ФИЗ ЛИЦА КЛИЕНТ**)_
3. В открывшемся окне ищем строку **`When Retrieving`**, в которой указано имя необходимого рула

![img3](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/12%20How%20to%20find%20rule/IMG/3.png?raw=true)


**_NOTE:_** В **git** репозитории, ровно как и в самих рулах, название пишется без префикса **`F_`**

4. Собственно по названию рула мы можем понять в какой **`Model`** оно используется,  далее соответственно название **`ViewModel`** и т.д. по цепочке.


<br/>

[back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/0%20Topics/README.md)