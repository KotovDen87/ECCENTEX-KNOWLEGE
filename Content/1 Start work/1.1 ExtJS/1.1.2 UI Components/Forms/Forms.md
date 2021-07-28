# FORMS

Форма не более чем стандартный контейнер для форм. По сути, это **`Panel`**. Панели форм могут использоваться во всем приложении, где есть потребность в сборе данных от пользователя.

Кроме того, панели форм могут использовать любую компоновку контейнера, обеспечивая удобный и гибкий способ управления позиционированием своих полей. Панели форм также могут быть привязаны к модели, что упрощает загрузку данных с сервера и их отправку обратно на сервер.

Пример формы реального проекта:

![img1](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.1%20ExtJS/1.1.2%20UI%20Components/Forms/IMG/1.png?raw=true)


Под капотом **Form Panel** находится базовая форма, которая обрабатывает все службы управления полями ввода, проверки, отправки и загрузки форм. Это означает, что многие параметры конфигурации базовой формы можно использовать непосредственно на панели формы.

### Панель базовой формы
Вот как создать простую форму для сбора пользовательских данных:
```JavaScript
    Ext.create('Ext.form.Panel', {
        renderTo: document.body,
        title: 'User Form',
        height: 350,
        width: 300,
        bodyPadding: 10,
        defaultType: 'textfield',
        items: [
            {
                fieldLabel: 'First Name',
                name: 'firstName'
            },
            {
                fieldLabel: 'Last Name',
                name: 'lastName'
            },
            {
                xtype: 'datefield',
                fieldLabel: 'Date of Birth',
                name: 'birthDate'
            }
        ]
    });
```

Эта форма отображается в теле документа и имеет три поля - «Имя», «Фамилия» и «Дата рождения». Поля добавляются на панель формы с помощью конфигурации элементов.

В **`fieldLabel`** определяет, какой текст будет отображаться в метке рядом с полем, и имя конфигурации становится **name** атрибутом базового HTML поля.

Обратите внимание, что эта панель формы имеет тип по умолчанию **`textfield`**. Это означает, что любые его элементы, для которых не указан **`xtype`** _(поля «Имя» и «Фамилия» в этом примере)_, являются текстовыми полями.

С другой стороны, у поля «Дата рождения» **`xtype`**  настроен как **`datefield`**, что делает его полем даты. Поля даты должны содержать только действительные данные даты и поставляться с **DatePicker** для выбора даты.

### Типы полей

**ExtJS** предоставляет набор стандартных типов полей из коробки:
  * Ext.form.field.Checkbox
  * Ext.form.field.ComboBox
  * Ext.form.field.Date
  * Ext.form.field.Display
  * Ext.form.field.File
  * Ext.form.field.Hidden
  * Ext.form.field.HtmlEditor
  * Ext.form.field.Number
  * Ext.form.field.Radio
  * Ext.form.field.Text
  * Ext.form.field.TextArea
  * Ext.form.field.Time


<br/>

_Более подробно с Панелями Форм **ExtJS** можно ознакомиться на [официальном сайте](https://docs.sencha.com/extjs/5.1.1/guides/components/forms.html)._


<br/>

[back to UI Components](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.1%20ExtJS/1.1.2%20UI%20Components/UI%20Components.md) | [back to ExtJS](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.1%20ExtJS/ExtJS.md) | [back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/0%20Topics/Topics.md)