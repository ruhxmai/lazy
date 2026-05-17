---
id: js-hoisting
category: Frontend
daily: true
---

# Что такое hoisting в JavaScript?

## Ответ

**Hoisting** — механизм JS, при котором объявления переменных и функций поднимаются в начало своей области видимости до выполнения кода.

```js
// var — поднимается, но значение undefined
console.log(name); // undefined
var name = 'Alice';

// let/const — поднимаются, но находятся в "temporal dead zone"
console.log(age); // ReferenceError
let age = 25;

// Function declaration — поднимается целиком
greet(); // "Hello!"
function greet() {
  console.log('Hello!');
}

// Function expression — НЕ поднимается
sayBye(); // TypeError: sayBye is not a function
var sayBye = function() {
  console.log('Bye!');
};
```

Вывод: используй `let`/`const` и объявляй функции до их вызова.
