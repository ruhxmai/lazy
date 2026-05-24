---
id: js-this
category: Frontend
daily: true
---
# Что такое `this` в JavaScript?
## Ответ
`this` — ключевое слово, указывающее на контекст вызова функции. Значение зависит от того, **как** вызвана функция.

| Контекст | Значение `this` |
|---|---|
| Глобальный (не strict) | `window` / `global` |
| Метод объекта | Сам объект |
| Arrow-функция | `this` из внешней области |
| `call` / `apply` / `bind` | Явно переданный объект |

```js
const obj = {
  name: 'Bob',
  greet() { console.log(this.name); }, // 'Bob'
  arrow: () => console.log(this),       // this из внешнего scope
};

obj.greet();         // Bob
obj.greet.call({ name: 'Alice' }); // Alice
```
