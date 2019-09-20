# Определение объекта

Обьект в JS – составное значение (НЕпримитивный тип данных)

**Объект** – это неупорядоченная коллекция свойств, где каждое свойство состоит из **имени(ключа)** и ассоциированного с ним **значения**.

Другие название для JS обьекта:

-   Ассоциативный массив
-   Словарь (dictionary)
-   Хеш (hash)

# Применение объекта

Объект предназначен для хранения сложных структур данных.

```js
var name = 'Andrei';
var surname = 'Ivanov';
var age = 18;
var position = 'developer';
```

Переменные выше описывают одну сущность – необходимо сгруппировать их в структуру данных, которая позволит:

-   иметь единую переменную для всего набора данных
-   удобно работать с данными (добавлять данные, удалять данные и искать данные)

```js
var user = {
    name: 'Andrei',
    surname: 'Ivanov',
    age: 18,
    position: 'developer',
};
```

# Инициализация объекта

Для инициализации объекта используется **объектный литерал** (aka декларативная форма).

Объектный литерал – `{ }` – первичной выражение, которое может содержать ноль или несколько пар свойств, которые состоят из комбинации ключ-значение.

```js
var obj = {};
var obj1 = {a: 1};
var obj2 = {
    a: 'hello',
    b: 123,
};
```

# Синтаксис объекта

```js
var obj = {prop1: 5};
```

где

-   `prop1: 5` – Свойство (property) объекта
-   `prop1` – Имя (ключ) свойства:
    -   _IdentifierName_
    -   _StringLiteral_
    -   _NumericLiteral_
-   `5` – Любое валидное выражение (все что может стоять справа от оператора равно (=)

> Пример

```js
var obj = {
    a: 1,
    hello: 2,
    '': 3,
    123: 4,
    var: 5,
};
```

# Свойство и метод

Если значение свойства объекта является функцией, то такое свойство именуется методом.

**Метод** – свойство, которое может быть **вызвано**!

```js
var obj = {
    a: 1,
    f: function() {
        console.log(1);
    },
};
```

# Доступ к свойствам объекта

Объекты являются ассоциативными массивами, т.е. каждое свойство ассоциировано с именем, через которое можно получить доступ к значению свойства.

**Обращаемся к имени(ключу) свойства объекта, чтобы получить значение данного свойства**

**Точечная нотация (dot notation):**
`object.IdentifierName`

**Скобочная нотация (bracket notation):**
`object[Expression]`

> Пример

```js
var obj = {
    myProp: 100,
    1: 200,
};
var key = 'myProp';

obj.myProp; // 100
obj['myProp']; // 100
obj[1]; // 200
obj[key]; // 100
```

Скобочная нотация также позволяет обратиться к свойству, имя которого хранится в переменной!

**Обращение к свойству – выражение!**

```js
var a = obj[key];
a; // 100
```

# Добавление, изменение и удаление свойства

Объекты в JS **динамические** – обычно позволяют добавлять и удалять свойства в любое время.

```js
var obj = {a: 1};

obj.a; // 1 – получаем значение
obj.a = 9; // устанавливаем новое значение
obj.a; // 9
obj.b = 100; // добавляем новое свойсво с ключом b и значением 100
// obj['b'] = 100; добавление нового свойства в скобочной нотации
```

Удаление свойства из объекта – **унарный оператор `delete`**

```js
delete obj.a; // данное выражение возвращает true
```

# Сравнение объектов

В то время как примитивные типы данных копируются и сравниваются **по значению**:

```js
var a = 'hello';
var b = a;
a === b; // true
a = 100;
a === b; // false
```

Объекты копируются и сравниваются **по ссылке**:

```js
var obj1 = {a: 1};
var obj2 = obj1;
obj1 === obj2; // true
obj1.b = 2;
obj1 === obj2; // true
```

# Существует ли свойство в объекте?

```js
var obj = {a: 1};
obj.b; // undefined

var obj = {a: 1, b: undefined};
obj.b; // undefined
```

Обращение к имени свойства, которое отсутствует в объекте возвращает значение `undefined`.

**НО!**
Есть вероятность, что существует свойство со значение `undefined`.

Оператор `in` – возвращает `true`, если свойство содержится в указанном объекте.

Синтаксис:

_expression_ **in** object

expression – выражение, которое возвращает имя(ключ), которое ищется в свойстве

**Поиск свойства в объекте осуществляется по его имени (ключу)!**

```js
var obj = {a: 1, c: undefined};
a in obj; // true
b in obj; // false
c in obj; // true
```

# Итерация по объекту

Инструкция `for...in` – проходит по перечисляемым свойствам объекта
Синтаксис:
**for (** _variableStatement_ **in** _object_ **)**

_variableStatement_ – объявляем переменную, в которую последовательно будут записаны все имена(ключи) свойств итерируемого объекта object

```js
var obj = {a: 1, b: 2};
for (var key in obj) {
    console.log(key);
}
// a
// b
for (var key in obj) {
    console.log(obj[key]);
}
// 1
// 2
```