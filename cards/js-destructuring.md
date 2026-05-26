---
id: js-destructuring
category: Frontend
difficulty: junior
daily: true
---

# Что такое деструктуризация в JavaScript?

## Ответ

Деструктуризация — синтаксис для извлечения значений из объектов и массивов в отдельные переменные.

```js
// Деструктуризация объекта
const user = { name: 'Alice', age: 25, city: 'Moscow' };
const { name, age } = user;
console.log(name); // 'Alice'

// Переименование переменной
const { name: userName } = user;

// Значение по умолчанию
const { role = 'user' } = user;

// Деструктуризация массива
const [first, second, ...rest] = [1, 2, 3, 4];
console.log(first); // 1
console.log(rest);  // [3, 4]

// В параметрах функции
function greet({ name, age }) {
  return `Hello, ${name}! Age: ${age}`;
}
```

- Позволяет писать более чистый и короткий код
- Часто используется при работе с API-ответами и пропсами в React
