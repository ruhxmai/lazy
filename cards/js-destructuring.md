---
id: js-destructuring
category: JavaScript
daily: true
---
# Что такое деструктуризация и оператор spread/rest?
## Ответ
**Деструктуризация** — синтаксис для извлечения значений из объектов и массивов в переменные.
**Spread (`...`)** — разворачивает итерируемый объект. **Rest** — собирает оставшиеся элементы.

```js
// Объект
const { name, age = 18, address: { city } } = user;

// Массив
const [first, , third] = [1, 2, 3];

// Rest в параметрах
function sum(...nums) {
  return nums.reduce((a, b) => a + b, 0);
}

// Spread — клонирование и слияние
const merged = { ...defaults, ...overrides };
const copy = [...arr, newItem];
```
