---
id: js-scope
category: JavaScript
daily: true
---
# Чем отличаются var, let и const по области видимости?

## Ответ

- `var` — функциональная область видимости, поднимается (hoisting) с `undefined`
- `let` — блочная область видимости, не инициализируется при hoisting (TDZ — Temporal Dead Zone)
- `const` — блочная область видимости, должна быть сразу инициализирована, не переприсваивается

```js
function example() {
  if (true) {
    var a = 1;   // доступна во всей функции
    let b = 2;   // доступна только в блоке if
    const c = 3; // доступна только в блоке if
  }
  console.log(a); // 1
  console.log(b); // ReferenceError: b is not defined
}
```
