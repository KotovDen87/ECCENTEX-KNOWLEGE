# ВОПРОСЫ НА СОБЕСЕДОВАНИИ ПО JAVASCRIP:

### 1) Типы данных в JS _(пока что их всего 8)_
  1. **string**
  1. **number**
  1. **bigint** _(bigint введен, чтобы дать разрабам работать с числами произвольной длины. индикатор бигинта `n` в конце числа)_
  1. **boolean**
  1. **symbol** _(уникальный идентификатор)_
  1. **object**
  _**7** и **8** - оба значения показывают отсутствующие данные_
  1. **null**  _(это отдельный тип, НО если проверить через оператор **typeof** получим в консоле **object**. Это ошибка которая сложилась исторически, об этом важно упамянуть)_
  1. **undefined**

#### под вопрос:
  * В чем разница между **null** и **undefined**?

### Разница между не строгим и строгим равенством ( == и === )
```JavaScript
  1 == '1' // true // не строгое - просто сравнивает значения
  1 === '1' // false // строгое - дополнительно сравнивает их тип данных
```
#### под вопрос:
  * что вернет **null == undefined**? _(тут будет true)_
  * что вернет **null === undefined**? _(тут будет false)_

### function declaration vs. function expression. В чем разница
  * function declaration - функция созданная в основном потоке документа
  * function expression - это когда созданная функция присваивается в переменную _(Объявление функции в контексте какого-либо присваивания)_

  **Основное отличие:** function declaration создается интерпритатором до выполнения кода, т.е. ее можно вызвать до ее объявления и не будет ошибки

  Пример:
```JavaScript
  // Execution
  sum(1,2) // 3
  multipl(1,2) // error

  // function declaration
  function sum(a,b){
    return a+b;
  }

  // function expression
  var multipl = function(a,b){
    return a*b;
  }
```

### ПРАКТИЧЕСКИЕ ЗАДАНИЯ:

1. Функция проверки палиндрома
```JavaScript
// Base lvl
// Advanced lvl
// ES6 lvl
```

1. Функция поиска самого короткого слова?
```JavaScript
// Base lvl
// Advanced lvl
// ES6 lvl
```

1. Функция создания инициалов?
```JavaScript
// Base lvl
// Advanced lvl
// ES6 lvl
```

1. Функция суммирования всех цифр числа?
```JavaScript
// Base lvl
// Advanced lvl
// ES6 lvl
```

1. Функция поиска минимального и максимального значений в массиве?\
```JavaScript
// Base lvl
// Advanced lvl
// ES6 lvl
```

1. Функция создания набора дубликатов символов строки?
```JavaScript
// Base lvl
// Advanced lvl
// ES6 lvl
```

1. Функция возврата индексов заглавных букв строки?
```JavaScript
// Base lvl
// Advanced lvl
// ES6 lvl
```

1. Функция вывода чисел от 1 до n (n - передаваемый аргумент)
```JavaScript
// Base lvl
// Advanced lvl
// ES6 lvl
```

1. Функция возврата уникальных значений из нескольких массивов?
```JavaScript
// Base lvl
// Advanced lvl
// ES6 lvl
```
