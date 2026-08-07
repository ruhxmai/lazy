---
id: js-json-methods
category: Frontend
difficulty: junior
daily: true
---

# Чем отличаются JSON.stringify и JSON.parse?

## Ответ

`JSON.stringify()` превращает JS-значение в **строку JSON**, `JSON.parse()` — делает обратное.

```js
const user = { name: 'Alex', age: 25, active: true };

const json = JSON.stringify(user);
// '{"name":"Alex","age":25,"active":true}'

const restored = JSON.parse(json);
// { name: 'Alex', age: 25, active: true }
```

**Подводные камни:**
- `undefined`, функции и `Symbol` при сериализации **пропадают**
- `JSON.stringify(obj, null, 2)` — красивый вывод с отступами (удобно для логов)
- `Date` превращается в строку, `JSON.parse` не восстанавливает её обратно в `Date` автоматически
- Циклические ссылки в объекте вызовут `TypeError`

```js
JSON.stringify({ a: undefined, b: () => {}, c: 1 });
// '{"c":1}' — a и b пропали
```
