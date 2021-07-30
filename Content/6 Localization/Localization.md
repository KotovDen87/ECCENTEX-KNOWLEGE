# 🌎 ЛОКАЛИЗАЦИЯ ИНТЕРФЕЙСА

### Локализация различных лэйблов или полей на формах/гридах
<details><summary><i><h7>click to expand!</h7></i></summary>

1. Переходим в **`Setup`** солюшена

![SolutionSetup](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/IMG/SolutionSetup.png?raw=true)

2. В сайдбаре **`Localization`** => **`Translations`**

![img1](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/6%20Localization/IMG/1.png?raw=true)


3. Ищем нужный ключ. Например, **Contact person (full name)**

![img2](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/6%20Localization/IMG/2.png?raw=true)

4. В комбобоксе **`Language`** выбираем нужный язык локализации _(в примере RUSSIAN)_. Ранее найденная нами запись станет **ссылкой** _(будет подсвечена синим)_, кликнув по которой откроется поле для ввода значения на выбранном языке

![img3](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/6%20Localization/IMG/3.png?raw=true)

5. Заполняем и жмем **`SAVE`**
6. После заполнения всех нужных локализаций жмем **`Publish`**


**_NOTE:_** _При создании локализации ДЕПЛОЙ не нужен._

**_NOTE:_** _Чтобы полю, лейблу и т.п. сделать перевод в JS коде пишем: **t(`‘SOME_TEXT’`)** . Далее выполняем поиск _(п.3)_ по ключу **SOME_TEXT** и далее по мануалу._

</details>

### Локализация основного интерфейса _(пункты меню)_
<details><summary><i><h7>click to expand!</h7></i></summary>

1. Переходим в **`Студия приложений`** и выбираем нужный **SOLUTION**

![AppStudio](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/IMG/AppStudio.png?raw=true)

2. В сайдбаре **`Localization`** => **`Localization Data`**

![img4](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/6%20Localization/IMG/4.png?raw=true)

3. В открывшемся окне ищем нужный нам пункт меню или создаем новый. _(Искать нужно вручную, нормального поиска нет 😔)_
4. После всех правок делаем [ДЕПЛОЙ](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/2%20Deploy/Deploy.md#%EF%B8%8F-%D0%B4%D0%B5%D0%BF%D0%BB%D0%BE%D0%B9)

</details>


<br/>

[back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/0%20Topics/Topics.md)