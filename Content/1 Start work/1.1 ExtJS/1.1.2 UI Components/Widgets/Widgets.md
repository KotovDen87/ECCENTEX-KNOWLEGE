# WIDGETS

Класс **`Ext.Widget`** или просто **`виджет`** - это легкий класс, но состоящий исключительно из **`Ext.dom.Element`** и **`listeners`**. Это отличает виджет от обычного компонента, поскольку класс **Ext.Widget** не является производным от **`Ext.Component`**. Компонент обеспечивает надежное управление жизненным циклом, которое добавляет огромное количество функциональных возможностей. Однако за эту функциональность приходится платить.

Несколько стандартных виджетов:
* Progress Bar _(Ext.Progress or "progressbarwidget")_
* Slider _(Ext.slider.Widget or "sliderwidget")_
* Sparklines _(Ext.sparkline.*)_
    * Line _("sparklineline")_
    * Bar _("sparklinebar")_
    * Discrete _("sparklinediscrete")_
    * Bullet _("sparklinebullet")_
    * Pie _("sparklinepie")_
    * Box _("sparklinebox")_
    * TriState _("sparklinetristate")_

### Использование виджетов

Как и в случае с обычными компонентами, к элементам контейнера можно добавлять виджеты. Например, мы можем добавить спарклайн на панель инструментов:
```JavaScript
  var panel = Ext.create({
      xtype: 'panel',
      title: 'Title',
      frame: true,
      renderTo: document.body,
      width: 250,
      height: 150,
      html: 'Some text',
      tbar: [{
          text: 'Button'
      }, '->', {
          xtype: 'sparklineline',
          fillColor: '#ddf',
          width: 100,
          height: 20,
          values: [2, 3, 0, 4, -1]
      }]
  });
```

![img1](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.1%20ExtJS/1.1.2%20UI%20Components/Widgets/IMG/1.png?raw=true)

В случае **`Sparklines`** вы должны указать размер _(**width** и **height**)_ или использовать для этого менеджер компоновки **Ext JS**. Потому что внутренние рисунки не имеют естественного размера.

### Столбец виджетов

**Столбец виджетов** позволяет легко отображать любой компонент или виджет в колонке грида. Добавление столбца виджетов не простое занятие. Назначьте колонке **xtype** **`widgetcolumn`** и задайте конфигурацию. Конфигурация является объектом, который содержит **xtype** для каждой ячейки. Этот **xtype** может относиться к любому классу **Ext.Widget** или **Ext.Component**.

Используя столбец виджетов для добавления виджетов в грид, вы можете выполнить впечатляющий объем визуализации данных, пример ниже:

![img2](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.1%20ExtJS/1.1.2%20UI%20Components/Widgets/IMG/2.png?raw=true)

В следующем примере на гриде мы добавим столбц виджетов, который содержит виджет индикатора выполнения _(добавляется к каждой строке)_.
```JavaScript
  var store = Ext.create('Ext.data.Store', {
      fields: ['name','progress'],
      data: [
          { name: 'Test 1', progress: 0.10 },
          { name: 'Test 2', progress: 0.23 },
          { name: 'Test 3', progress: 0.86 },
          { name: 'Test 4', progress: 0.31 }
      ]
  });

  Ext.create({
      xtype: 'grid',
      title: 'Widget Column Demo',
      store: store,

      columns: [{
          text: 'Test Number',
          dataIndex: 'name',
          width: 100
      }, {
          xtype: 'widgetcolumn',
          text: 'Progress',
          width: 120,
          dataIndex: 'progress',
          widget: {
              xtype: 'progressbarwidget',
              textTpl: '{value:percent}'
          }
      }],

      width: 220,
      height: 250,
      renderTo: document.body
  });
```

Итог:

![img3](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.1%20ExtJS/1.1.2%20UI%20Components/Widgets/IMG/3.png?raw=true)


<br/>

_Более подробно с **Ext.Widget** можно ознакомиться на [официальном сайте](https://docs.sencha.com/extjs/5.1.1/guides/components/widgets_widgets_columns.html)._


<br/>

[back to UI Components](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.1%20ExtJS/1.1.2%20UI%20Components/UI%20Components.md#-ui-%D0%BA%D0%BE%D0%BC%D0%BF%D0%BE%D0%BD%D0%B5%D0%BD%D1%82%D1%8B) | [back to ExtJS](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.1%20ExtJS/ExtJS.md#%EF%B8%8F-extjs-511) | [back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/0%20Topics/Topics.md)