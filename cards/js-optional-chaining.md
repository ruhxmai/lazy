---
id: js-optional-chaining
category: Frontend
difficulty: junior
daily: true
---

# Что делают операторы `?.` и `??` в JavaScript?

## Ответ

- `?.` (**optional chaining**) — безопасно обращается к свойству или вызывает метод, останавливаясь и возвращая `undefined`, если промежуточное значение `null`/`undefined`, вместо выброса ошибки.
- `??` (**nullish coalescing**) — возвращает правый операнд, только если левый `null` или `undefined` (в отличие от `||`, который срабатывает и на `0`, `''`, `false`).

```js
const user = { profile: null };

console.log(user.profile?.name); // undefined, без ошибки
console.log(user.profile.name);  // TypeError: Cannot read properties of null

const count = 0;
console.log(count || 10); // 10 — ловушка, 0 считается falsy
console.log(count ?? 10); // 0  — только null/undefined заменяются
```

- Работает и с вызовом функций: `obj.method?.()`
- Можно комбинировать в цепочку: `user.profile?.address?.city ?? 'Неизвестно'`
