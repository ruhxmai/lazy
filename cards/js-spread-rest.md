---
id: js-spread-rest
category: JavaScript
daily: true
---
# Чем отличается spread (...) от rest (...) в JavaScript?
## Ответ
**Rest** (`...`) — собирает несколько аргументов в массив (используется в параметрах функции).
**Spread** (`...`) — раскрывает массив или объект в отдельные элементы.

```js
// Rest: собирает аргументы в массив
function sum(...nums) {
  return nums.reduce((a, b) => a + b, 0);
}
sum(1, 2, 3); // 6

// Spread: раскрывает массив
const a = [1, 2];
const b = [...a, 3, 4]; // [1, 2, 3, 4]

// Spread с объектами (shallow copy)
const user = { name: 'Alice' };
const admin = { ...user, role: 'admin' };
// { name: 'Alice', role: 'admin' }
```

Оба используют `...`, но контекст определяет смысл: rest — в определении параметров, spread — в вызове или литерале.
