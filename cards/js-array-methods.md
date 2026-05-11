---
id: js-array-methods
category: Frontend
daily: true
---

# Чем отличаются map(), filter() и reduce()?

## Ответ

Все три метода не изменяют исходный массив.

```js
const nums = [1, 2, 3, 4, 5];

// map — преобразует каждый элемент, возвращает массив той же длины
const doubled = nums.map(n => n * 2);         // [2, 4, 6, 8, 10]

// filter — оставляет элементы, прошедшие условие
const evens = nums.filter(n => n % 2 === 0);  // [2, 4]

// reduce — сворачивает массив в одно значение
const sum = nums.reduce((acc, n) => acc + n, 0); // 15
```

`map` → новый массив той же длины. `filter` → подмножество. `reduce` → одно значение любого типа.
