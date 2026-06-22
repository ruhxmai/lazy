---
id: js-hoisting
category: JavaScript
daily: true
---
# Что такое hoisting в JavaScript?
## Ответ
Hoisting (поднятие) — механизм JavaScript, при котором объявления переменных и функций "поднимаются" в начало своей области видимости до выполнения кода.

- `var` — поднимается и инициализируется как `undefined`
- `let` / `const` — поднимаются, но **не инициализируются** (Temporal Dead Zone)
- Function declaration — поднимается целиком вместе с телом

```js
console.log(a); // undefined (не ошибка!)
var a = 5;

console.log(b); // ReferenceError: Cannot access 'b' before initialization
let b = 10;

greet(); // "Hello!" (функция поднята целиком)
function greet() { console.log("Hello!"); }

foo(); // TypeError: foo is not a function
var foo = function() {}; // function expression ведёт себя как var
```
