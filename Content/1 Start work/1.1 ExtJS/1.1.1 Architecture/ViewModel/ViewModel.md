# ViewModel

  Этот класс управляет произвольными данными и их отношениями к моделям данных. Экземпляры **ViewModel** связаны с некоторыми компонентами, а затем используются их дочерними элементами для привязки данных.

### Привязка

  Наиболее часто используемый аспект **ViewModel** - это **`bind`** метод. Этот метод принимает "**bind descriptor**" и обратный вызов для вызова, когда данные, указанные дескриптором привязки _(bind descriptor)_, становятся доступными или изменяются.

  **`bind`** метод, основанный на связывания заданного дескриптора, будет возвращать различные типы "привязанных" объектов. Эти объекты поддерживают связь между запрошенными данными и обратным вызовом. В конечном итоге привязки являются производными, из **`Ext.app.bind.BaseBinding`** которых предоставляется несколько методов, помогающих управлять привязкой.

  Пожалуй, самый важный метод **`destroy`**. Когда привязка больше не нужна, важно помнить об **destroy**. Утечка привязок может вызвать проблемы с производительностью или даже хуже, если обратные вызовы вызываются в неожиданное время.

### Stores

  **`Stores`** могут быть созданы как часть определения **`ViewModel`**. Определения обрабатываются как привязки, что обеспечивает очень мощную динамическую функциональность.

  Важно убедиться, что вы называете ключи данных **viewModel** уникальным образом. Если данные не имеют однозначного имени, привязки и формулы могут получать информацию из непреднамеренного источника данных. Это относится к ключам в блоке данных **viewModel**, конфигурациях хранилищ и ссылок.
  ```JavaScript
  var viewModel = new Ext.app.ViewModel({
      stores: {
          users: {
              model: 'User',
              autoLoad: true,
              filters: [{
                  property: 'createdDate',
                  value: '{createdFilter}',
                  operator: '>'
              }]
          }
      }
  });
  // Later on in our code, we set the date so that the store is created.
  viewModel.set('createdFilter', Ext.Date.subtract(new Date(), Ext.Date.DAY, 7));
  ```


<br/>

_Более подробно с **Ext.app.ViewModel** можно ознакомиться на [официальном сайте](https://docs.sencha.com/extjs/5.1.1/api/Ext.app.ViewModel.html)._


<br/>

[back to Architecture](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.1%20ExtJS/1.1.1%20Architecture/Architecture.md) | [back to ExtJS](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.1%20ExtJS/ExtJS.md) | [back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/0%20Topics/Topics.md)