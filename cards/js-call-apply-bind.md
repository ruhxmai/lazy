---
id: js-call-apply-bind
category: Frontend
difficulty: junior
daily: true
---

# Чем отличаются call, apply и bind?

## Ответ

Все три метода позволяют явно указать значение `this` для функции, но работают по-разному.

- `call(thisArg, arg1, arg2, ...)` — вызывает функцию сразу, аргументы через запятую
- `apply(thisArg, [args])` — вызывает функцию сразу, аргументы массивом
- `bind(thisArg, ...)` — **не вызывает** функцию, а возвращает новую с привязанным `this`

```js
function greet(greeting) {
  console.log(`${greeting}, ${this.name}`);
}

const user = { name: 'Alex' };

greet.call(user, 'Hi');      // Hi, Alex — вызов сразу
greet.apply(user, ['Hi']);   // Hi, Alex — вызов сразу
const bound = greet.bind(user);
bound('Hi');                 // Hi, Alex — вызов позже
```

**Мнемоника:** call — Comma, apply — Array, bind — Later.
