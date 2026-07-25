---
id: js-truthy-falsy
category: Frontend
daily: true
---

# Что такое truthy и falsy значения в JavaScript?

## Ответ

В JS любое значение можно привести к `boolean` в условиях (`if`, `&&`, `||`). **Falsy** — значения, которые превращаются в `false`. Их всего 8, остальное — **truthy**.

```js
// Falsy-значения (запомнить все 8):
false, 0, -0, 0n, "", null, undefined, NaN

// Всё остальное — truthy, даже это:
Boolean([])        // true
Boolean({})         // true
Boolean("0")        // true (непустая строка!)
Boolean("false")    // true
```

Частая ошибка джуниора — проверять число на `0` через `if (!value)`:

```js
function setCount(value) {
  if (!value) value = 10; // баг: setCount(0) тоже станет 10!
}

// Правильно:
function setCount(value) {
  if (value === undefined) value = 10;
}
```

- `&&` возвращает первое falsy-значение или последнее операнд
- `||` возвращает первое truthy-значение
- `??` (nullish coalescing) реагирует только на `null`/`undefined`, а не на любые falsy
