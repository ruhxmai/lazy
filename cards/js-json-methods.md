---
id: js-json-methods
category: Frontend
difficulty: junior
daily: true
---

# Как преобразовать объект в JSON и обратно в JavaScript?

## Ответ

`JSON.stringify()` превращает JS-объект в строку JSON, `JSON.parse()` — делает обратное.

```js
const user = { name: "Alex", age: 25, isAdmin: false };

const json = JSON.stringify(user);
// '{"name":"Alex","age":25,"isAdmin":false}'

const obj = JSON.parse(json);
// { name: "Alex", age: 25, isAdmin: false }
```

**Частые ловушки:**
- `undefined`, функции и `Symbol` игнорируются при `stringify`
- `JSON.stringify(obj, null, 2)` — красивый вывод с отступами
- Циклические ссылки вызывают `TypeError`
- Даты превращаются в строки — нужно вручную вызывать `new Date(str)` после парсинга

```js
JSON.stringify({ a: undefined, b: () => {}, c: 1 });
// '{"c":1}' — undefined и функция пропали
```
