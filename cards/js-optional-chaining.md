---
id: js-optional-chaining
category: Frontend
daily: true
---
# Что такое optional chaining (?.) и nullish coalescing (??) в JS?
## Ответ
`?.` безопасно обращается к вложенным свойствам — возвращает `undefined` вместо ошибки, если значение `null` или `undefined`.

`??` возвращает правый операнд только если левый — `null`/`undefined` (в отличие от `||`, который срабатывает на любое falsy-значение: `0`, `''`, `false`).

```js
const city = user?.address?.city;       // undefined, если нет address
const fn   = obj?.method?.();           // вызов метода если он существует

const name  = user?.name ?? 'Гость';   // 'Гость' если null/undefined
const count = data.count ?? 0;          // 0 только если null/undefined, не если 0
```
