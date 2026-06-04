---
id: js-spread-rest
category: JavaScript
daily: true
---
# Чем отличается spread от rest в JavaScript?

## Ответ
Оба используют синтаксис `...`, но в разных контекстах:

- **Spread (`...`)** — разворачивает итерируемое значение в отдельные элементы (при вызове/создании)
- **Rest (`...`)** — собирает оставшиеся элементы в массив (в параметрах/деструктуризации)

```js
// Spread: разворачивает
const a = [1, 2, 3];
const b = [...a, 4, 5]; // [1, 2, 3, 4, 5]
Math.max(...a);         // 3

const obj1 = { x: 1 };
const obj2 = { ...obj1, y: 2 }; // { x: 1, y: 2 }

// Rest: собирает
function sum(...nums) { // nums = [1, 2, 3]
  return nums.reduce((acc, n) => acc + n, 0);
}
sum(1, 2, 3); // 6

const [first, ...rest] = [10, 20, 30];
// first = 10, rest = [20, 30]
```
