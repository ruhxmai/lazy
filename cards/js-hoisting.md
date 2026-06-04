---
id: js-hoisting
category: JavaScript
daily: true
---
# Что такое hoisting (поднятие) в JavaScript?

## Ответ
Hoisting — механизм, при котором объявления переменных и функций «поднимаются» в начало своей области видимости до выполнения кода.

- `var` — поднимается и инициализируется как `undefined`
- `let` / `const` — поднимаются, но находятся в «мёртвой зоне» (TDZ) до строки объявления
- Функции (function declaration) — поднимаются полностью, включая тело

```js
console.log(x); // undefined (не ошибка)
var x = 5;

console.log(y); // ReferenceError: Cannot access 'y' before initialization
let y = 10;

greet(); // "Hello!" — функция доступна до объявления
function greet() {
  console.log("Hello!");
}
```
