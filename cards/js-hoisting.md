---
id: js-hoisting
category: Frontend
difficulty: junior
daily: true
---

# Что такое hoisting (поднятие) в JavaScript?

## Ответ

Hoisting — механизм JS, при котором **объявления переменных и функций** перемещаются в начало области видимости до выполнения кода.

```js
console.log(x); // undefined — не ошибка
var x = 5;

greet(); // "Hello" — функция работает до объявления
function greet() {
  console.log("Hello");
}

console.log(y); // ReferenceError
let y = 10;    // let/const находятся в Temporal Dead Zone
```

`var` поднимается и инициализируется как `undefined`. `let`/`const` поднимаются, но остаются в **Temporal Dead Zone** до строки объявления — обращение к ним до этого бросает ошибку.
