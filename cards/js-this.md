---
id: js-this
category: Frontend
daily: true
---
# Что такое `this` в JavaScript?
## Ответ
`this` — ссылка на объект, в контексте которого выполняется функция. Значение зависит от способа вызова.

| Контекст | Значение `this` |
|---|---|
| Глобальный | `window` (или `undefined` в strict mode) |
| Метод объекта | Сам объект |
| `new Func()` | Новый экземпляр |
| Arrow-функция | `this` из внешнего контекста |

```js
const obj = {
  name: 'Bob',
  greet() { console.log(this.name); }, // 'Bob'
  arrow: () => console.log(this),       // window / undefined
};

const greet = obj.greet;
greet();        // undefined (потерян контекст)
greet.call(obj); // 'Bob'
```
