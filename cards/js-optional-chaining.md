---
id: js-optional-chaining
category: JavaScript
difficulty: junior
daily: true
---

# Что делает оператор `?.` и чем `??` отличается от `||`?

## Ответ

**Optional chaining `?.`** — безопасно обращается к свойству или методу, возвращая `undefined` вместо ошибки, если значение `null`/`undefined`.

```js
const user = null;
console.log(user?.name);          // undefined (без ошибки)
console.log(user?.address?.city); // undefined

const arr = null;
console.log(arr?.[0]);            // undefined
console.log(obj?.method?.());     // undefined
```

**Nullish coalescing `??`** — возвращает правое значение только если левое `null` или `undefined` (в отличие от `||`, который срабатывает на любое falsy-значение).

```js
const count = 0;
console.log(count || 10); // 10  ← неожиданно!
console.log(count ?? 10); // 0   ← правильно

const name = null;
console.log(name ?? 'Гость'); // 'Гость'
```

Часто используются вместе: `user?.profile?.bio ?? 'Нет описания'`
