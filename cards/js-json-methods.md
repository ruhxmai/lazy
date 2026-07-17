---
id: js-json-methods
category: Frontend
difficulty: junior
daily: true
---

# Как работают `JSON.stringify` и `JSON.parse` в JavaScript?

## Ответ

`JSON.stringify(value)` превращает JS-значение в строку JSON, `JSON.parse(str)` — делает обратное.

```js
const user = { name: "Ann", age: 25, isAdmin: false };

const json = JSON.stringify(user);
// '{"name":"Ann","age":25,"isAdmin":false}'

const obj = JSON.parse(json);
// { name: "Ann", age: 25, isAdmin: false }
```

**Что теряется при `stringify`:**

```js
JSON.stringify({
  a: undefined,        // ключ пропадёт
  b: function () {},   // ключ пропадёт
  c: Symbol("x"),       // ключ пропадёт
  d: NaN,               // станет null
  e: new Date(),         // станет строкой ISO
});
// '{"d":null,"e":"2026-07-17T00:00:00.000Z"}'
```

**Полезные параметры:**

```js
// Красивый вывод с отступом в 2 пробела
JSON.stringify(user, null, 2);

// Второй аргумент — replacer, фильтрует/трансформирует поля
JSON.stringify(user, ["name"]); // '{"name":"Ann"}'

// Циклическая ссылка — TypeError: Converting circular structure to JSON
const obj2 = {};
obj2.self = obj2;
JSON.stringify(obj2); // ❌ бросает исключение
```

`structuredClone(obj)` — современная альтернатива для глубокого клонирования, которая не теряет `undefined`, `Date`, `Map`, `Set` в отличие от `JSON.parse(JSON.stringify(obj))`.
