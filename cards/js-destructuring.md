---
id: js-destructuring
category: Frontend
daily: true
---
# Что такое деструктуризация в JavaScript?
## Ответ
Деструктуризация — синтаксис для извлечения значений из массивов и свойств объектов в отдельные переменные.

**Объект:**
```js
const { name, age } = { name: 'Alice', age: 25 };
// name === 'Alice', age === 25

// Переименование и дефолт:
const { name: userName = 'Guest' } = {};
```

**Массив:**
```js
const [first, second, ...rest] = [1, 2, 3, 4];
// first=1, second=2, rest=[3,4]
```

**Spread / Rest:**
```js
const merged = { ...obj1, ...obj2 }; // spread — объединяет
function sum(...nums) { }            // rest — собирает аргументы
```
