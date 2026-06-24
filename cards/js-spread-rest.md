---
id: js-spread-rest
category: Frontend
daily: true
---

# Что такое операторы spread и rest в JavaScript?

## Ответ

**Spread (`...`)** — разворачивает массив/объект в отдельные элементы.  
**Rest (`...`)** — собирает оставшиеся аргументы в массив.

```js
// Spread — копирование и слияние
const a = [1, 2, 3];
const b = [...a, 4, 5]; // [1, 2, 3, 4, 5]

const obj1 = { x: 1 };
const obj2 = { ...obj1, y: 2 }; // { x: 1, y: 2 }

// Rest — в функциях
function sum(...nums) {
  return nums.reduce((acc, n) => acc + n, 0);
}
sum(1, 2, 3); // 6

// Rest — в деструктуризации
const [first, ...rest] = [10, 20, 30];
// first = 10, rest = [20, 30]
```

Spread используется **при вызове**, rest — **при объявлении**.
