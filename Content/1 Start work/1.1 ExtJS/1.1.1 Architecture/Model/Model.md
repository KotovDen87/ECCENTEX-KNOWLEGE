# Model

  Модель представляют собой некоторый объект, которым управляет ваше приложение. Например, можно определить модель для пользователей, продуктов, автомобилей или другого объекта реального мира, который мы хотим смоделировать в системе. Модели используются **Ext.data.Store** , которые, в свою очередь, используются многими компонентами с привязкой к данным в Ext.


### Fields

  Модели определяются как набор полей и любых произвольных методов и свойств, относящихся к модели. Например:
```JavaScript
  Ext.define('User', {
      extend: 'Ext.data.Model',
      fields: [
          {name: 'name',  type: 'string'},
          {name: 'age',   type: 'int', convert: null},
          {name: 'phone', type: 'string'},
          {name: 'alive', type: 'boolean', defaultValue: true, convert: null}
      ],

      changeName: function() {
          var oldName = this.get('name'),
              newName = oldName + " The Barbarian";

          this.set('name', newName);
      }
  });
```

  Теперь мы можем создавать экземпляры нашей модели User и вызывать любую определенную нами логику модели:
```JavaScript
  var user = Ext.create('User', {
      id   : 'ABCD12345',
      name : 'Conan',
      age  : 24,
      phone: '555-555-5555'
  });

  user.changeName();
  user.get('name'); //returns "Conan The Barbarian"
```

  По умолчанию встроенные типы полей, такие как числовые и логические строковые значения приведения в необработанных данных, в силу их метода **Ext.data.field.Field#method-convert**. Если сервер может отправлять данные в формате, который не нужно преобразовывать, отключение этого параметра может улучшить производительность. **Ext.data.reader.Json** и **Ext.data.reader.Array** являются вероятными кандидатами для этой оптимизации. Чтобы отключить преобразование полей, вы просто указываете `null` в конфигурации преобразования поля.

#### Поле "id" и idProperty

  Определение модели всегда имеет _поле идентификации_, которое должно давать уникальный ключ для каждого экземпляра. По умолчанию поле с именем **`id`** будет создано с отображением **`id`**. Это происходит из-за `idProperty` по умолчанию, предоставленного в определениях модели.

  Чтобы изменить, какое поле является полем идентификации, используйте конфигурацию **idProperty**.


### Validators

  Модели имеют встроенную поддержку валидаторов полей. Валидаторы добавляются к моделям, как в следующем примере:
```JavaScript
  Ext.define('User', {
      extend: 'Ext.data.Model',
      fields: [
          { name: 'name',     type: 'string' },
          { name: 'age',      type: 'int' },
          { name: 'phone',    type: 'string' },
          { name: 'gender',   type: 'string' },
          { name: 'username', type: 'string' },
          { name: 'alive',    type: 'boolean', defaultValue: true }
      ],

      validators: {
          age: 'presence',
          name: { type: 'length', min: 2 },
          gender: { type: 'inclusion', list: ['Male', 'Female'] },
          username: [
              { type: 'exclusion', list: ['Admin', 'Operator'] },
              { type: 'format', matcher: /([a-z]+)[0-9]{2,3}/i }
          ]
      }
  });
```

  Производный тип **`Ext.data.field.Field`** также может обеспечивать валидацию. Если необходимо продублировать несколько полей, рассмотрите возможность создания настраиваемого типа поля.

#### Validation

  Результаты валидаторов можно получить через «связанную» запись валидации:
```JavaScript
  var instance = Ext.create('User', {
      name: 'Ed',
      gender: 'Male',
      username: 'edspencer'
  });

  var validation = instance.getValidation();
```

  Возвращенный объект является экземпляром `Ext.data.Validation` и имеет в качестве своих полей результат поля **validators**. Объект валидации является "**грязным**", если присутствует одна или несколько ошибок валидации.

  Эта запись также доступна при использовании привязки данных в качестве "**псевдо-ассоциации**", называемой "**validation**". Псевдо-ассоциация может быть скрыта явно объявленной ассоциацией с тем же именем _(из соображений совместимости)_, но делать это не рекомендуется.

  `Ext.Component#modelValidation` конфигурации могут быть использованы для того, чтобы автоматического связывания от "**validation**" в запись к полям формы, которые могут быть связаны с его значениями.


### Ассоциации

  Модели часто связаны с другими моделями. Эти ассоциации могут быть определены полями _(часто называемыми **внешними ключами**)_ или другими данными, такими как «многие-ко-многим».


### Использование Store

  Очень часто возникает желание загрузить набор экземпляров модели для отображения и управления ими в пользовательском интерфейсе. Мы делаем это, создавая **Ext.data.Store**:
```JavaScript
  var store = Ext.create('Ext.data.Store', {
      model: 'User'
  });

  //uses the Proxy we set up on Model to load the Store data
  store.load();
```

  Store - это просто набор экземпляров модели, обычно загружаемых откуда-то с сервера. Store также может поддерживать набор добавленных, обновленных и удаленных экземпляров модели для синхронизации с сервером через прокси.


<br/>

_Более подробно с **Ext.data.Model** можно ознакомиться на [официальном сайте](https://docs.sencha.com/extjs/5.1.1/api/Ext.data.Model.html)._


<br/>

[back to Architecture](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.1%20ExtJS/1.1.1%20Architecture/Architecture.md#-%D0%B0%D1%80%D1%85%D0%B8%D1%82%D0%B5%D0%BA%D1%82%D1%83%D1%80%D0%B0-%D0%BF%D1%80%D0%B8%D0%BB%D0%BE%D0%B6%D0%B5%D0%BD%D0%B8%D0%B9) | [back to ExtJS](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.1%20ExtJS/ExtJS.md#%EF%B8%8F-extjs-511) | [back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/0%20Topics/Topics.md)