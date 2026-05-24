---
id: js-destructuring
category: Frontend
daily: true
---
# Что такое деструктуризация в JavaScript?
## Ответ
Деструктуризация — синтаксис, позволяющий «распаковать» значения из массивов или свойства из объектов в отдельные переменные.

**Объект:**
```js
const { name, age } = { name: 'Alice', age: 30 };
console.log(name); // 'Alice'
```

**Массив:**
```js
const [first, second] = [10, 20, 30];
console.log(first); // 10
```

**Псевдоним и значение по умолчанию:**
```js
const { name: userName = 'Guest' } = {};
console.log(userName); // 'Guest'
```
