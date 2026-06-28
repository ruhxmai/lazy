---
id: js-optional-chaining
category: JavaScript
daily: true
---
# Что делает оператор ?. (optional chaining) и ?? (nullish coalescing)?
## Ответ
**Optional chaining (?.)** позволяет безопасно обращаться к вложенным свойствам объекта, не получая ошибку если промежуточное значение `null` или `undefined`.

**Nullish coalescing (??)** возвращает правый операнд, если левый — `null` или `undefined` (в отличие от `||`, который реагирует на любое falsy).

```js
const user = null;

// Без optional chaining — ошибка!
// user.address.city // TypeError

// С optional chaining
console.log(user?.address?.city); // undefined

// Nullish coalescing
const city = user?.address?.city ?? 'Unknown';
console.log(city); // 'Unknown'

// Вызов методов
const name = user?.getName?.(); // undefined (без ошибки)

// Доступ к элементу массива
const first = user?.tags?.[0]; // undefined

// ?? vs ||
console.log(0 || 'default');  // 'default' (0 — falsy)
console.log(0 ?? 'default');  // 0        (0 — не null/undefined)
```
