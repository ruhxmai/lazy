---
id: js-destructuring
category: JavaScript
daily: true
---
# Что такое деструктуризация в JavaScript?
## Ответ
Деструктуризация — способ извлекать значения из массивов и объектов в отдельные переменные за одну строку.

```js
// Объект
const { name, age } = { name: 'Alice', age: 25 };

// Массив
const [first, second] = [10, 20];

// Переименование и значение по умолчанию
const { title: label = 'Unknown' } = {};

// Вложенный объект
const { address: { city } } = { address: { city: 'Moscow' } };

// В параметрах функции
function greet({ name, role = 'user' }) {
  return `Hello, ${name} (${role})`;
}
```
