---
id: js-generators
category: Frontend
daily: true
---
# Что такое генераторы в JavaScript?
## Ответ
Генератор — функция, которая может **приостанавливать** выполнение через `yield` и возобновлять его.

```javascript
function* counter() {
  yield 1;
  yield 2;
  yield 3;
}

const gen = counter();
gen.next(); // { value: 1, done: false }
gen.next(); // { value: 2, done: false }
gen.next(); // { value: 3, done: false }
gen.next(); // { value: undefined, done: true }
```

Применяется для: ленивых последовательностей, бесконечных итераторов, пошаговой обработки данных.
