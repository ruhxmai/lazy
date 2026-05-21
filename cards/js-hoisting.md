---
id: js-hoisting
category: JavaScript
daily: true
---
# Что такое hoisting в JavaScript?
## Ответ
Hoisting — это механизм, при котором **объявления** переменных и функций «поднимаются» наверх области видимости до выполнения кода.

- `var` — поднимается и инициализируется как `undefined`
- `let` / `const` — поднимаются, но остаются в «мёртвой зоне» (TDZ) до строки объявления
- Функции-объявления поднимаются целиком (имя + тело)

```js
console.log(a); // undefined (не ошибка)
var a = 5;

console.log(b); // ReferenceError: Cannot access 'b' before initialization
let b = 5;

greet(); // "Hello" — работает
function greet() { console.log("Hello"); }

sayBye(); // TypeError — только переменная поднята, не значение
var sayBye = () => console.log("Bye");
```
