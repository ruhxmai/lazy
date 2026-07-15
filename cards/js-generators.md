---
id: js-generators
category: Frontend
difficulty: junior
daily: true
---

# Что такое генераторы (generators) в JavaScript?

## Ответ

**Генератор** — специальная функция (`function*`), которая может **приостанавливать** своё выполнение через `yield` и возобновлять его позже. В отличие от обычной функции, она не выполняется вся целиком сразу, а возвращает **итератор**.

```js
function* range(start, end) {
  for (let i = start; i <= end; i++) {
    yield i;
  }
}

const it = range(1, 3);
it.next(); // { value: 1, done: false }
it.next(); // { value: 2, done: false }
it.next(); // { value: 3, done: false }
it.next(); // { value: undefined, done: true }

for (const n of range(1, 3)) {
  console.log(n); // 1, 2, 3
}
```

Каждый вызов `next()` выполняет код до ближайшего `yield` и «замораживает» состояние функции — локальные переменные сохраняются между вызовами.

Полезны для **ленивых вычислений** (бесконечные последовательности), кастомных итераторов и как основа для `async`/`await` (который под капотом похож на генераторы с промисами).
