# СОЗДАНИЕ НОВОЙ СТРАНИЦЫ В САЙДБАРЕ

1. Переходим в **`Студия приложений`** и выбираем нужный **SOLUTION**
2. В сайдбаре **`Applications`** => **`User Applications`**
3. В открывшемся окне кликаем нужный ресурс
4. И в том месте где необходимо добавить линк кликаем правой кнопкой и жмем **`Add Page`**

![img1](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/5%20New%20page/IMG/1.png?raw=true)

5. Заполняем поля и жмем Сохранить

![img2](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/5%20New%20page/IMG/2.png?raw=true)

**_Инструкция по заполнению:_**
  * В **`MENU LABEL`** пишем название в таком формате **_@Resource('Solution:`НАЗВАНИЕ_ЛЭЙБЛА`')@_**
  * **`PAGE`** - шаблон страницы. Обычно используется **UNTIL_BasePage**

  ![img3](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/5%20New%20page/IMG/3.png?raw=true)

  * В параметре **`app`** пишем название созданного в репозитории файла с префиксом **_App_**, но в данном поле пишем его без префикса
  * В **`usePageConfig`** пишем **1** _(константа)_
  * В **`group`** пишем **SD**
  * В **`API Permanent ID`** в инпуте пишем тоже самое что и писали в **`НАЗВАНИЕ_ЛЭЙБЛА`**

6. На вкладке **`Item ermissions`** заполняем нужные **_Permissions_** и сохраняем.
7. В сайдбаре **`Localization`** => **`Localization Data`**
8. Создаем новую переменную:
    * `Resource Key` = **НАЗВАНИЕ_ЛЭЙБЛА**
    * Название линки на разных языках _(то что вы напишите в переводах, будет отражено в UI)_
9. [Деплоим](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/2%20Deploy/README.md) изменения


<br/>

**_Пример:_**

Нужно создать создать страницу **_“справочник Hold Days”_**

![img4](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/5%20New%20page/IMG/4.png?raw=true)

Как видно на скрине в **MENU LABEL** указали **_@Resource('Solution:`SD_ACTIVITYDAYSHOLD`')@_**

В параметре **`app`** указали **_CLLDaysHold_** и в **`API Permanent ID`** _ROOT_SD_CLL_SD_COLLECTION_`SD_ACTIVITYDAYSHOLD`_

Далее переходим в репозиторий проекта:  _`app`_ => _`SolutionSysFiles`_ => _`SD`_ => _`JS`_

И создаем соответствующий JS файл с префиксом _APP_ => **_CLLDaysHoldApp.js_**

В котором указана ссылка на **Panel**, которая рендерит нам страницу

![img5](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/5%20New%20page/IMG/5.png?raw=true)

**_LifeHack:_** _Для теста корректности созданию в этом файле можно указать ссылку на уже созданную и стабильно работающую **Panel**._


<br/>

[back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/0%20Topics/README.md)