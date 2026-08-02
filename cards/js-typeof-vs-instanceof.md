---
id: js-typeof-vs-instanceof
category: Frontend
difficulty: junior
daily: true
---

# Чем `typeof` отличается от `instanceof` в JavaScript?

## Ответ

`typeof` возвращает **строку** с примитивным типом значения, `instanceof` проверяет, является ли объект **экземпляром** конкретного конструктора (по цепочке прототипов).

```js
typeof 42;             // "number"
typeof "hi";            // "string"
typeof undefined;       // "undefined"
typeof null;            // "object"  — исторический баг JS!
typeof [];               // "object"
typeof function(){};     // "function"

[] instanceof Array;    // true
[] instanceof Object;   // true (Array наследуется от Object)
"hi" instanceof String; // false — примитив, не объект-обёртка
```

- `typeof` хорош для примитивов, но не различает `null`, массивы, объекты — все дают `"object"`
- `instanceof` работает только с объектами и проверяет `prototype`-цепочку, не годится для примитивов
- Чтобы точно узнать, массив ли значение, используйте `Array.isArray(value)`

Итог: для примитивов — `typeof`, для проверки класса объекта — `instanceof` (или `Array.isArray`).
