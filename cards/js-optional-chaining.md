---
id: js-optional-chaining
category: Frontend
difficulty: junior
daily: true
---

# Что делает оператор `?.` и чем `??` отличается от `||`?

## Ответ

**Optional chaining `?.`** — безопасный доступ к свойствам. Если значение слева `null` или `undefined`, возвращает `undefined` вместо выброса ошибки.

**Nullish coalescing `??`** — возвращает правый операнд только если левый равен `null` или `undefined`. Оператор `||` срабатывает на любое falsy-значение (`0`, `''`, `false`).

```js
const user = null;

// Без ?. — ошибка
user.address.city; // TypeError: Cannot read properties of null

// С ?. — безопасно
user?.address?.city; // undefined

// ?? vs ||
const count = 0;
console.log(count || 10); // 10  (0 — falsy, срабатывает)
console.log(count ?? 10); // 0   (0 — не null/undefined, не срабатывает)

// Комбинация: получить значение или дефолт
const port = config?.server?.port ?? 3000;
```

- `?.` — прерывает цепочку при `null`/`undefined`, возвращает `undefined`
- `??` — fallback только для `null` и `undefined`, а не для всех falsy
