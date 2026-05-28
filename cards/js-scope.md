---
id: js-scope
category: Frontend
difficulty: junior
daily: true
---

# Что такое hoisting и чем отличаются var, let и const?

## Ответ

**Hoisting** — механизм, при котором объявления переменных и функций «поднимаются» в начало области видимости до выполнения кода.

- `var` — поднимается и инициализируется как `undefined`, область видимости — функция
- `let` / `const` — поднимаются, но находятся в **Temporal Dead Zone (TDZ)** до строки объявления; область видимости — блок `{}`

```js
console.log(a); // undefined — var hoisted
var a = 5;

console.log(b); // ReferenceError: Cannot access 'b' before initialization
let b = 10;

function greet() {
  console.log(msg); // undefined
  var msg = 'hello';
}
```

**Правило:** используй `const` по умолчанию, `let` — если нужна перезапись, `var` — никогда.
