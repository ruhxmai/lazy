---
id: js-destructuring
category: Frontend
difficulty: junior
daily: true
---

# Что такое деструктуризация в JavaScript?

## Ответ

Деструктуризация — синтаксис для извлечения значений из массивов и объектов в отдельные переменные.

```js
// Объект
const user = { name: 'Alice', age: 25, city: 'Moscow' };
const { name, age } = user;
console.log(name); // 'Alice'

// С переименованием и значением по умолчанию
const { name: userName, role = 'guest' } = user;

// Массив
const [first, second, ...rest] = [1, 2, 3, 4, 5];
console.log(first); // 1
console.log(rest);  // [3, 4, 5]

// В параметрах функции
function greet({ name, age }) {
  return `${name} is ${age}`;
}
```

- Работает с объектами и массивами
- Поддерживает значения по умолчанию и псевдонимы
- Rest-оператор `...` собирает оставшиеся элементы
