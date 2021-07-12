# Model

Модель или сущность представляют собой некоторый объект, которым управляет ваше приложение. Например, можно определить модель для пользователей, продуктов, автомобилей или другого объекта реального мира, который мы хотим смоделировать в системе. Модели используются **Ext.data.Store** , которые, в свою очередь, используются многими компонентами с привязкой к данным в Ext.

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

По умолчанию встроенные типы полей, такие как числовые и логические строковые значения приведения в необработанных данных, в силу их метода Ext.data.field.Field # method-convert . Если сервер может отправлять данные в формате, который не нужно преобразовывать, отключение этого параметра может улучшить производительность. В Ext.data.reader.Json и Ext.data.reader.Array читателей являются вероятными кандидатами для этой оптимизации. Чтобы отключить преобразование полей, вы просто указываете `null` в конфигурации преобразования поля.

##### Поле "id" и idProperty

Определение модели всегда имеет _поле идентификации_, которое должно давать уникальный ключ для каждого экземпляра. По умолчанию поле с именем **`id`** будет создано с отображением **`id`**. Это происходит из-за `idProperty` по умолчанию, предоставленного в определениях модели.

Чтобы изменить, какое поле является полем идентификации, используйте конфигурацию **idProperty**.

### Валидаторы

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

Производный тип `Ext.data.field.Field` также может обеспечивать проверку. Если `validators` необходимо продублировать несколько полей, рассмотрите возможность создания настраиваемого типа поля.

##### Проверка

Результаты валидаторов можно получить через «связанную» запись валидации:
```JavaScript
var instance = Ext.create('User', {
    name: 'Ed',
    gender: 'Male',
    username: 'edspencer'
});

var validation = instance.getValidation();
```

Возвращенный объект является экземпляром `Ext.data.Validation` и имеет в качестве своих полей результат поля `validators`. Объект проверки является «грязным», если присутствует одна или несколько ошибок проверки.

Эта запись также доступна при использовании привязки данных в качестве «псевдо-ассоциации», называемой «проверка». Эта псевдо-ассоциация может быть скрыта явно объявленной ассоциацией с тем же именем (из соображений совместимости), но делать это не рекомендуется.

`Ext.Component#modelValidation` Конфигурации могут быть использованы для того, чтобы автоматического связывания от «проверки» в запись к полям формы , которые могут быть связаны с его значениями.


### Ассоциации

Модели часто связаны с другими моделями. Эти ассоциации могут быть определены полями (часто называемыми «внешними ключами») или другими данными, такими как «многие-ко-многим» (или «матрица»).

Ассоциации с иностранными ключами - один ко многим
Самый простой способ определить связь одной модели с другой - добавить эталонную конфигурацию в соответствующее поле.
```JavaScript
 Ext.define('Post', {
     extend: 'Ext.data.Model',

     fields: [
         { name: 'user_id', reference: 'User' }
     ]
 });

 Ext.define('Comment', {
     extend: 'Ext.data.Model',

     fields: [
         { name: 'user_id', reference: 'User' },
         { name: 'post_id', reference: 'Post' }
     ]
 });

 Ext.define('User', {
     extend: 'Ext.data.Model',

     fields: [
         'name'
     ]
 });
 ```

Размещение referenceв соответствующих полях сообщает модели, какое поле имеет внешний ключ, и тип модели, которую он идентифицирует. То есть значение этих полей устанавливается равным значению idProperty поля целевой Модели.

Один ко многим без внешних ключей
Для того, чтобы определить связь без внешнего ключа поля, вам нужно будет использовать либо cfg-hasMany или cfg-belongsTo.
```JavaScript
 Ext.define('Post', {
     extend: 'Ext.data.Model',

     belongsTo: 'User'
 });

 Ext.define('Comment', {
     extend: 'Ext.data.Model',

     belongsTo: [ 'Post', 'User' ]
 });

 // User is as above
 ```

Эти объявления немного изменились по сравнению с предыдущими выпусками. В предыдущих выпусках обе «стороны» ассоциации должны были заявить о своих конкретных ролях. Теперь это требуется только в том случае, если значения по умолчанию, принятые для имен, неудовлетворительны.

Ассоциации с иностранными ключами - один на один
Частным случаем ассоциаций «один ко многим» является случай «один к одному». Это определяется как unique reference.
```JavaScript
 Ext.define('Address', {
     extend: 'Ext.data.Model',

     fields: [
         'address',
         'city',
         'state'
     ]
 });

 Ext.define('User', {
     extend: 'Ext.data.Model',

     fields: [{
         name: 'addressId',
         reference: 'Address',
         unique: true
     }]
 });
 ```

Многие ко многим
Классический вариант использования "многие ко многим" - это пользователь и группа. Пользователи могут принадлежать ко многим группам, а группы могут содержать много пользователей. Эта ассоциация объявляется с использованием cfg-manyToManyконфигурации следующим образом:
```JavaScript
 Ext.define('User', {
     extend: 'Ext.data.Model',

     fields: [
         'name'
     ],

     manyToMany: 'Group'
 });

 Ext.define('Group', {
     extend: 'Ext.data.Model',

     fields: [
         'name'
     ],

     manyToMany: 'User'
 });
 ```

Как и в случае с другими ассоциациями, нужно указать только одну «сторону».

Для управления отношениями между manyToManyотношениями необходимо использовать Ext.data.Session .

Использование прокси
Модели отлично подходят для представления типов данных и отношений, но рано или поздно мы захотим где-нибудь загрузить или сохранить эти данные. Вся загрузка и сохранение данных осуществляется через Ext.data.proxy.Proxy , который можно установить непосредственно в модели:
```JavaScript
Ext.define('User', {
    extend: 'Ext.data.Model',
    fields: ['id', 'name', 'email'],

    proxy: {
        type: 'rest',
        url : '/users'
    }
});
```

Здесь мы настроили Ext.data.proxy.Rest , который знает, как загружать и сохранять данные в бэкэнд RESTful и обратно. Посмотрим, как это работает:
```JavaScript
var user = Ext.create('User', {name: 'Ed Spencer', email: 'ed@sencha.com'});

user.save(); //POST /users
```

Вызов save в новом экземпляре модели сообщает настроенному RestProxy, что мы хотим сохранить данные этой модели на нашем сервере. RestProxy выясняет, что эта модель не была сохранена ранее, потому что у нее нет идентификатора, и выполняет соответствующее действие - в этом случае отправляет запрос POST на настроенный нами URL (/ users). Мы настраиваем любой прокси для любой модели и всегда следуем этому API - см. Ext.data.proxy.Proxy для полного списка.

Загрузка данных через прокси выполняется статическим loadметодом:
```JavaScript
//Uses the configured RestProxy to make a GET request to /users/123
User.load(123, {
    success: function(user) {
        console.log(user.getId()); //logs 123
    }
});
```

Модели также можно легко обновлять и уничтожать:
```JavaScript
//the user Model we loaded in the last snippet:
user.set('name', 'Edward Spencer');

//tells the Proxy to save the Model. In this case it will perform a PUT request to /users/123 as this Model already has an id
user.save({
    success: function() {
        console.log('The User was updated');
    }
});

//tells the Proxy to destroy the Model. Performs a DELETE request to /users/123
user.erase({
    success: function() {
        console.log('The User was destroyed!');
    }
});
```
Имена параметров HTTP при использовании Ext.data.proxy.Ajax
По умолчанию идентификатор модели указывается в параметре HTTP с именем id. Чтобы изменить имя этого параметра, используйте конфигурацию idParam прокси .

Также могут быть настроены параметры для других часто передаваемых значений, таких как номер страницы или начальная строка .

Использование в магазинах
Очень часто возникает желание загрузить набор экземпляров модели для отображения и управления ими в пользовательском интерфейсе. Мы делаем это, создавая Ext.data.Store :
```JavaScript
var store = Ext.create('Ext.data.Store', {
    model: 'User'
});

//uses the Proxy we set up on Model to load the Store data
store.load();
```

Магазин - это просто набор экземпляров модели, обычно загружаемых откуда-то с сервера. Магазин также может поддерживать набор добавленных, обновленных и удаленных экземпляров модели для синхронизации с сервером через прокси. Дополнительную информацию о магазинах см. В Ext.data.Store .