---
id: js-hoisting
category: JavaScript
difficulty: junior
daily: true
---

# Что такое hoisting в JavaScript?

## Ответ

Hoisting (поднятие) — поведение JS, при котором объявления переменных и функций «поднимаются» вверх своей области видимости до выполнения кода.

- **`var`** — поднимается и инициализируется как `undefined`
- **`let` / `const`** — поднимаются, но не инициализируются → **Temporal Dead Zone (TDZ)**
- **`function` declaration** — поднимается целиком, можно вызвать до объявления

```js
console.log(a); // undefined
var a = 5;

console.log(b); // ReferenceError: Cannot access 'b' before initialization
let b = 10;

greet(); // "Hello!" — function declaration поднимается полностью
function greet() {
  console.log("Hello!");
}

sayBye(); // TypeError: sayBye is not a function
var sayBye = function() { console.log("Bye!"); };
```

`const` и `let` находятся в TDZ с начала блока до строки объявления — обращение к ним в TDZ бросает `ReferenceError`.
