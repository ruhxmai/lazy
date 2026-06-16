---
id: js-hoisting
category: JavaScript
daily: true
---
# Что такое hoisting в JavaScript?

## Ответ

Hoisting — механизм, при котором **объявления** переменных и функций поднимаются в начало области видимости перед выполнением кода.

- `var` поднимается и инициализируется как `undefined`
- `let` / `const` поднимаются, но остаются в **Temporal Dead Zone** до строки объявления
- Function declaration поднимается целиком — можно вызвать до объявления
- Function expression (через `var`) поднимается только переменная, не функция

```js
console.log(a); // undefined (не ошибка)
var a = 5;

console.log(b); // ReferenceError: Cannot access 'b' before initialization
let b = 5;

hello(); // "Hello!" — function declaration поднимается
function hello() { console.log("Hello!"); }

world(); // TypeError: world is not a function
var world = function() {};
```
