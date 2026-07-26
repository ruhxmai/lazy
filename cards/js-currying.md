---
id: js-currying
category: JavaScript
difficulty: junior
daily: true
---

# Что такое каррирование (currying) в JavaScript?

## Ответ

Каррирование — это преобразование функции с несколькими аргументами в цепочку функций, каждая из которых принимает **один аргумент**.

```js
function multiply(a, b, c) {
  return a * b * c;
}

function curriedMultiply(a) {
  return (b) => (c) => a * b * c;
}

multiply(2, 3, 4);          // 24
curriedMultiply(2)(3)(4);   // 24
```

Каррирование удобно для создания специализированных функций из общих:

```js
const double = curriedMultiply(2)(1);
double(5); // 10
```

- Позволяет **частично применять** аргументы заранее.
- Используется в функциональном программировании и композиции функций (`compose`, `pipe`).
- Не путать с `bind` — `bind` фиксирует `this` и часть аргументов, но не превращает функцию в цепочку унарных вызовов.
