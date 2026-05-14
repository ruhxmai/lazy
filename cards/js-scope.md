---
id: js-scope
category: Frontend
difficulty: junior
daily: true
---

# Чем отличаются var, let и const по области видимости?

## Ответ

**var** — функциональная область видимости, поднимается (hoisting) с `undefined`.
**let** и **const** — блочная область видимости (`{}`), не инициализируются при hoisting (TDZ — Temporal Dead Zone).
**const** — нельзя переприсвоить, но объект/массив можно мутировать.

```js
function example() {
  if (true) {
    var a = 1;   // видна во всей функции
    let b = 2;   // видна только в блоке {}
    const c = 3; // видна только в блоке {}
  }
  console.log(a); // 1
  console.log(b); // ReferenceError: b is not defined
}
```

- `var` — избегай в современном коде
- `let` — для переменных, которые меняются
- `const` — для всего по умолчанию
