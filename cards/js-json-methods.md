---
id: js-json-methods
category: Frontend
daily: true
---

# Как работают JSON.stringify и JSON.parse и какие у них подводные камни?

## Ответ

`JSON.stringify()` превращает JS-значение в JSON-строку, `JSON.parse()` — обратно в объект.

```js
const user = { name: "Аня", age: 25 };
const str = JSON.stringify(user); // '{"name":"Аня","age":25}'
const obj = JSON.parse(str);      // { name: "Аня", age: 25 }
```

**Подводные камни `JSON.stringify`:**

```js
JSON.stringify({ a: undefined });      // '{}'          — undefined пропадает
JSON.stringify({ fn: () => {} });      // '{}'          — функции пропадают
JSON.stringify({ d: new Date() });     // '{"d":"2026-..."}' — Date → строка
JSON.stringify({ n: NaN, i: Infinity }); // '{"n":null,"i":null}'

const obj = {};
obj.self = obj;
JSON.stringify(obj); // ❌ TypeError: Converting circular structure to JSON
```

**Полезные вторые/третьи аргументы:**

```js
// replacer — фильтрует ключи
JSON.stringify(user, ["name"]); // '{"name":"Аня"}'

// space — форматирование с отступами
JSON.stringify(user, null, 2);

// reviver в JSON.parse — трансформирует значения при разборе
JSON.parse('{"date":"2026-01-01"}', (key, value) =>
  key === "date" ? new Date(value) : value
);
```

> Частая ошибка: `JSON.parse()` на невалидной строке (например, `undefined` из `localStorage.getItem`) кидает `SyntaxError` — всегда оборачивай в `try/catch`.
