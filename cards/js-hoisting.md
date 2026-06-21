---
id: js-hoisting
category: JavaScript
daily: true
---
# Что такое hoisting (поднятие) в JavaScript?
## Ответ
Hoisting — механизм, при котором объявления переменных и функций «поднимаются» наверх своей области видимости до выполнения кода.

- `var` — поднимается и инициализируется как `undefined`
- `let` / `const` — поднимаются, но **не** инициализируются (Temporal Dead Zone)
- Function declaration — поднимается полностью (имя + тело)
- Function expression / Arrow — поднимается только переменная

```js
console.log(a); // undefined
var a = 5;

console.log(b); // ReferenceError: TDZ
let b = 5;

greet(); // "Hello" — works
function greet() { console.log("Hello"); }

sayHi(); // TypeError: sayHi is not a function
var sayHi = () => console.log("Hi");
```
