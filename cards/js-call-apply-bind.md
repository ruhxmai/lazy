---
id: js-call-apply-bind
category: Frontend
difficulty: junior
daily: true
---

# Чем отличаются call, apply и bind?

## Ответ

Все три метода задают значение `this` для функции, но по-разному:

- **call(thisArg, arg1, arg2, ...)** — вызывает функцию сразу, аргументы передаются по одному
- **apply(thisArg, [args])** — вызывает функцию сразу, аргументы передаются массивом
- **bind(thisArg, arg1, ...)** — НЕ вызывает функцию, а возвращает новую функцию с зафиксированным `this`

```js
function greet(greeting) {
  console.log(`${greeting}, ${this.name}`);
}

const user = { name: 'Alice' };

greet.call(user, 'Hi');    // Hi, Alice — вызов сразу
greet.apply(user, ['Hi']); // Hi, Alice — вызов сразу, аргументы массивом

const bound = greet.bind(user);
bound('Hi'); // Hi, Alice — вызов позже
```

Запомнить порядок: **C**all — аргументы через **c**omma, **A**pply — **a**rray, **B**ind — вызов **b**ackup на потом.
