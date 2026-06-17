---
id: js-hoisting
category: Frontend
difficulty: junior
daily: true
---

# Что такое hoisting в JavaScript?

## Ответ

**Hoisting** — механизм, при котором объявления переменных и функций «поднимаются» в начало области видимости до выполнения кода.

- `var` — поднимается и инициализируется значением `undefined`
- `let` / `const` — поднимаются, но не инициализируются (Temporal Dead Zone)
- `function` — поднимается **целиком**, функция доступна сразу

```js
console.log(a); // undefined — не ошибка
var a = 5;

console.log(b); // ReferenceError: Cannot access 'b' before initialization
let b = 5;

greet(); // "Hello!" — функция доступна до объявления
function greet() {
  console.log("Hello!");
}

sayBye(); // TypeError: sayBye is not a function
var sayBye = function () {
  console.log("Bye!");
};
```
