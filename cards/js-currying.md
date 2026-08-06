---
id: js-currying
category: Frontend
daily: true
---

# Что такое каррирование (currying) в JavaScript?

## Ответ

**Каррирование** — техника, при которой функция с несколькими аргументами превращается в цепочку функций, каждая из которых принимает по одному аргументу.

```js
// Обычная функция
function add(a, b, c) {
  return a + b + c;
}
add(1, 2, 3); // 6

// Каррированная версия
function curry(a) {
  return function (b) {
    return function (c) {
      return a + b + c;
    };
  };
}
curry(1)(2)(3); // 6

// То же самое через стрелочные функции
const curryAdd = a => b => c => a + b + c;
curryAdd(1)(2)(3); // 6
```

**Зачем это нужно:**
- Частичное применение — можно "заморозить" часть аргументов и переиспользовать функцию
- Более читаемые конфигурируемые функции

```js
const multiply = a => b => a * b;

const double = multiply(2);
double(5);  // 10
double(10); // 20
```
