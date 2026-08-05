---
id: js-currying
category: Frontend
difficulty: junior
daily: true
---

# Что такое каррирование (currying) в JavaScript?

## Ответ

Каррирование — это техника, при которой функция с несколькими аргументами превращается в **цепочку функций**, каждая из которых принимает один аргумент.

```js
function multiply(a) {
  return (b) => a * b;
}

const double = multiply(2);
double(5); // 10
multiply(3)(4); // 12
```

Каррирование удобно для создания специализированных функций из общих (частичное применение) и часто используется в функциональном программировании.

```js
const curry = (fn) => (a) => (b) => fn(a, b);
const add = curry((a, b) => a + b);
add(2)(3); // 5
```
