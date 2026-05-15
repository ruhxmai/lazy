---
id: js-hoisting
category: JavaScript
daily: true
---
# Что такое hoisting (поднятие) в JavaScript?
## Ответ
Hoisting — механизм JavaScript, при котором объявления переменных и функций «поднимаются» в начало своей области видимости до выполнения кода.

- `var` поднимается и инициализируется как `undefined`
- `let` и `const` поднимаются, но остаются в «временной мёртвой зоне» (TDZ) — обращение к ним до объявления выбрасывает `ReferenceError`
- Объявления функций поднимаются полностью вместе с телом

```js
console.log(a); // undefined — var hoisted
var a = 5;

console.log(b); // ReferenceError — let в TDZ
let b = 10;

greet(); // "Hello" — function declaration hoisted
function greet() { console.log("Hello"); }

hi(); // TypeError — function expression не поднимается
var hi = function() { console.log("Hi"); };
```
