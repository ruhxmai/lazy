---
id: js-optional-chaining
category: Frontend
difficulty: junior
daily: true
---

# Что такое optional chaining (?.) и nullish coalescing (??)?

## Ответ

**Optional chaining `?.`** — безопасное обращение к свойству: возвращает `undefined` вместо ошибки, если объект равен `null` или `undefined`.

**Nullish coalescing `??`** — возвращает правый операнд, если левый равен `null` или `undefined` (не просто falsy).

```js
const user = null;

// Без optional chaining — ошибка!
// user.profile.name // TypeError

console.log(user?.profile?.name); // undefined

// Nullish coalescing
const name = user?.name ?? "Гость"; // "Гость"

// Отличие от ||
const count = 0 ?? 10;  // 0  — ноль не является null/undefined
const count2 = 0 || 10; // 10 — ноль является falsy

// Optional chaining с методами
const len = user?.getName?.(); // undefined (не ошибка)
```
