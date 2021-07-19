# GRIDS

**`Ext.grid.Panel`** - одна из центральных составляющих **ExtJS**. Это невероятно универсальный компонент, который обеспечивает простой способ отображения, сортировки, группировки и редактирования данных.

Пример грида с реального проекта:

![img1](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.1%20ExtJS/UI%20Components/Grids/IMG/1.png?raw=true)

Пример создания простой формы:
```JavaScript
    Ext.create('Ext.grid.Panel', {
        renderTo: document.body,
        store: userStore,
        width: 400,
        height: 200,
        title: 'Application Users',
        columns: [
            {
                text: 'Name',
                width: 100,
                sortable: false,
                hideable: false,
                dataIndex: 'name'
            },
            {
                text: 'Email Address',
                width: 150,
                dataIndex: 'email',
                hidden: true
            },
            {
                text: 'Phone Number',
                flex: 1,
                dataIndex: 'phone'
            }
        ]
    });
```
В данном примере мы создали **`Ext.grid.Panel`**, который отображает себя в элементе **body**. Мы также сказали панели **`Grid`** получать данные из **`userStore`**.
Как видно из примера, у всех колонок есть свойство **`dataIndex`**, оно связывает поле из нашей модели со столбцом.

Столбец **`Name`** имеет фиксированную width из **100px** и выкл сортировкой. Столбец **`Email Address`** скрыт по умолчанию _(он может быть показан с помощью меню на заголовке любого другого столбца)_. Наконец, столбец **`Phone Number`** растягивается на всю оставшуюся ширину панели.

<br/>

_Более подробно с **Ext.grid.Panel** можно ознакомиться на [официальном сайте](https://docs.sencha.com/extjs/5.1.1/guides/components/grids.html)._