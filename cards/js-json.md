---
id: js-json
category: Frontend
difficulty: junior
daily: true
---

# Как сериализовать объект в JSON и обратно в JS?

## Ответ

`JSON.stringify()` превращает объект/массив в строку JSON, `JSON.parse()` — обратно в объект.

```js
const user = { name: "Alex", age: 25 };
const str = JSON.stringify(user); // '{"name":"Alex","age":25}'
const obj = JSON.parse(str);      // { name: "Alex", age: 25 }
```

Важно: `JSON.stringify` **теряет** функции, `undefined` и `Symbol`, а `Date` превращает в строку. Циклические ссылки вызовут ошибку.

```js
JSON.stringify({ fn: () => {}, a: undefined, b: 1 });
// '{"b":1}' — fn и a пропали
```
