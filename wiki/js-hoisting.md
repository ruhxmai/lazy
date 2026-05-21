---
title: JavaScript Hoisting
category: JavaScript
---
# JavaScript Hoisting

Hoisting — это поведение JavaScript-движка, при котором **объявления** переменных и функций перемещаются в начало своей области видимости на этапе компиляции (до выполнения кода). Важно понимать: поднимается только **объявление**, но не **присвоение**.

## Как это работает

### var
`var` объявляется и инициализируется значением `undefined` при подъёме.

```js
console.log(x); // undefined — не ошибка!
var x = 10;
console.log(x); // 10
```

### let и const
`let` и `const` тоже поднимаются, но попадают в **Temporal Dead Zone (TDZ)** — зону, в которой обращение к переменной вызывает `ReferenceError`.

```js
console.log(y); // ReferenceError: Cannot access 'y' before initialization
let y = 5;
```

### Функции-объявления
Поднимаются полностью — с именем и телом. Можно вызвать до объявления.

```js
sayHi(); // "Hi!" — работает
function sayHi() { console.log("Hi!"); }
```

### Функции-выражения и стрелочные функции
При присвоении в `var` — поднимается только переменная (значение `undefined`), вызов до объявления даёт `TypeError`.

```js
sayBye(); // TypeError: sayBye is not a function
var sayBye = function() { console.log("Bye!"); };
```

## Схема

```mermaid
flowchart TD
    A[Код запущен] --> B[Фаза компиляции]
    B --> C{Тип объявления}
    C -->|var| D[Поднять + инициализировать undefined]
    C -->|let / const| E[Поднять в TDZ без инициализации]
    C -->|function declaration| F[Поднять целиком: имя + тело]
    C -->|function expression / arrow| G[Поднять переменную со значением undefined]
    D --> H[Фаза выполнения]
    E --> H
    F --> H
    G --> H
    H --> I{Обращение до присвоения?}
    I -->|var| J[Вернуть undefined]
    I -->|let / const| K[ReferenceError: TDZ]
    I -->|function decl| L[Вызов работает]
    I -->|function expr| M[TypeError: not a function]
```

## Советы

- Всегда объявляй переменные **в начале** области видимости, чтобы избежать путаницы.
- Предпочитай `const` и `let` вместо `var` — их поведение более предсказуемо.
- Помни: `let`/`const` в TDZ — это не «не поднято», а «поднято, но недоступно».

## Карточки
- Что такое hoisting в JavaScript?
- Чем отличается поведение `var` от `let`/`const` при hoisting?
- Что такое Temporal Dead Zone (TDZ)?
- Можно ли вызвать function declaration до её объявления в коде?
