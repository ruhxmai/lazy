---
id: js-destructuring
category: Frontend
difficulty: junior
daily: true
---

# Что такое деструктуризация в JavaScript?

## Ответ

Деструктуризация — синтаксис для распаковки значений из массивов или свойств из объектов в отдельные переменные.

```js
// Объект
const user = { name: 'Alice', age: 25 };
const { name, age } = user;

// Переименование и значение по умолчанию
const { name: userName = 'Guest' } = user;

// Массив
const [first, second, ...rest] = [1, 2, 3, 4];

// В параметрах функции
function greet({ name, age = 0 }) {
  return `${name}, ${age}`;
}
```

- Упрощает работу с объектами и массивами
- Часто используется в React (props, useState, хуки)
