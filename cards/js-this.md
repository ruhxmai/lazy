---
id: js-this
category: Frontend
daily: true
---

# Что такое `this` в JavaScript?

## Ответ

`this` — контекст выполнения функции. Его значение зависит от **способа вызова**, а не места объявления.

```js
// Метод объекта — this = объект
const user = {
  name: 'Alice',
  greet() {
    console.log(this.name); // 'Alice'
  },
};
user.greet();

// Стрелочная функция — this из внешнего контекста
const obj = {
  name: 'Bob',
  greet: () => console.log(this.name), // undefined
};
```

Стрелочные функции **не имеют своего `this`** — они берут его из лексического окружения.
