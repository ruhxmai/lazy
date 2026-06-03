---
id: js-this
category: JavaScript
difficulty: junior
daily: true
---

# Что такое `this` в JavaScript и как определить его значение?

## Ответ

`this` — ссылка на объект-контекст, которая зависит от **того, как** вызвана функция, а не где она определена.

| Контекст вызова | Значение `this` |
|---|---|
| Глобальная область | `window` / `undefined` (strict mode) |
| Метод объекта | Объект перед точкой |
| Arrow-функция | `this` из внешней (лексической) области |
| `call` / `apply` / `bind` | Явно переданный объект |

```js
const user = {
  name: "Alice",
  greet() {
    console.log(this.name); // "Alice"
  },
  greetArrow: () => {
    console.log(this.name); // undefined — arrow берёт this снаружи
  },
};

user.greet();       // Alice
user.greetArrow();  // undefined

const fn = user.greet;
fn(); // undefined — потерян контекст
```

> Arrow-функции **не имеют своего** `this` — они захватывают его из лексической области при создании.
