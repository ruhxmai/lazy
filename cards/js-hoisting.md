---
id: js-hoisting
category: JavaScript
daily: true
---
# Что такое hoisting в JavaScript?
## Ответ
Hoisting — поведение JS, при котором объявления переменных и функций «поднимаются» в начало области видимости до выполнения кода.

```js
console.log(x); // undefined — не ошибка!
var x = 5;

greet(); // "Hello!" — вызов до объявления работает
function greet() {
  console.log("Hello!");
}

console.log(y); // ReferenceError: TDZ
let y = 10;
```

- `var` — поднимается, инициализируется `undefined`
- `let` / `const` — поднимаются, но остаются в TDZ (Temporal Dead Zone)
- `function declaration` — поднимается полностью вместе с телом
