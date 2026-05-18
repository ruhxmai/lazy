---
id: js-scope
category: Frontend
daily: true
---

# Чем отличаются var, let и const? Что такое hoisting?

## Ответ

`var` — функциональная область видимости, всплывает (hoisting), можно переопределить.  
`let` — блочная область, не всплывает (TDZ), можно переприсвоить.  
`const` — блочная, не всплывает, нельзя переприсвоить (но объект мутировать можно).

```js
console.log(a); // undefined — var всплыл
var a = 1;

console.log(b); // ReferenceError — TDZ (Temporal Dead Zone)
let b = 2;

const obj = { x: 1 };
obj.x = 2; // OK — мутация разрешена
obj = {};  // TypeError — переприсвоение запрещено
```

**Hoisting** — движок JS поднимает объявления переменных и функций в начало области видимости до выполнения кода. `var` всплывает со значением `undefined`; `let`/`const` всплывают, но остаются в TDZ до строки объявления.
