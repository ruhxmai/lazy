---
id: js-null-vs-undefined
category: Frontend
daily: true
---

# В чём разница между `null` и `undefined` в JavaScript?

## Ответ

`undefined` — значение по умолчанию: переменная объявлена, но не присвоена, отсутствующий аргумент функции или несуществующее свойство объекта. `null` — это **явно присвоенное** «пустое значение», разработчик сам решил, что здесь ничего нет.

```js
let a;
console.log(a); // undefined — не присвоено

let b = null;
console.log(b); // null — присвоено намеренно

typeof undefined; // "undefined"
typeof null;      // "object" (историческая ошибка в JS)

null == undefined;  // true  — нестрогое сравнение считает их равными
null === undefined; // false — разные типы
```

Правило: используй `null`, когда хочешь явно обнулить значение, а `undefined` оставляй как признак «значение ещё не задано».
