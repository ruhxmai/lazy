---
id: js-hoisting
category: JavaScript
daily: true
---
# Что такое hoisting (поднятие) в JavaScript?
## Ответ
Hoisting — механизм JS, при котором объявления переменных и функций «поднимаются» в начало своей области видимости до выполнения кода.

```js
console.log(x); // undefined — не ошибка, var поднялся
var x = 5;

greet(); // "Hello!" — function declaration поднялась целиком
function greet() {
  console.log("Hello!");
}

console.log(y); // ReferenceError: Cannot access 'y' before initialization
let y = 10;
```

- `var` — поднимается и инициализируется `undefined`
- `let` / `const` — поднимаются, но попадают в **temporal dead zone (TDZ)** до строки объявления
- `function declaration` — поднимается полностью (имя + тело)
- `function expression` / стрелочные функции — ведут себя как переменные
