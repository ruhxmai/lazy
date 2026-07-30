---
id: js-json-methods
category: Frontend
difficulty: junior
daily: true
---

# Как работают JSON.stringify и JSON.parse?

## Ответ

`JSON.stringify()` превращает JS-объект в строку, `JSON.parse()` — строку обратно в объект.

```js
const user = { name: 'Alex', age: 25, isAdmin: false };

const str = JSON.stringify(user);
// '{"name":"Alex","age":25,"isAdmin":false}'

const obj = JSON.parse(str);
// { name: 'Alex', age: 25, isAdmin: false }
```

**Частые ловушки:**

```js
JSON.stringify(undefined);           // undefined (не строка!)
JSON.stringify({ a: undefined });    // '{}' — поле пропадёт
JSON.stringify({ a: function(){} }); // '{}' — функции игнорируются
JSON.stringify({ date: new Date() }); // дата станет строкой ISO

JSON.parse('not json');              // SyntaxError — нужен try/catch
```

`stringify` умеет форматировать вывод и фильтровать поля:

```js
JSON.stringify(user, null, 2);         // с отступами в 2 пробела
JSON.stringify(user, ['name']);        // только поле name
```

Частое применение — глубокое клонирование (с ограничениями: теряются функции, `undefined`, `Date` превращается в строку):

```js
const clone = JSON.parse(JSON.stringify(user));
```
