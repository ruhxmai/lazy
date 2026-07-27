---
id: js-typeof-vs-instanceof
category: Frontend
daily: true
---

# Чем отличаются typeof и instanceof в JavaScript?

## Ответ

`typeof` возвращает **строку** с примитивным типом значения. Работает быстро, но с ловушками:

```js
typeof 42;          // "number"
typeof "hi";         // "string"
typeof true;         // "boolean"
typeof undefined;    // "undefined"
typeof null;         // "object"   ← исторический баг языка!
typeof [];            // "object"   ← массивы это тоже "object"
typeof {};            // "object"
typeof function(){};  // "function"
```

`instanceof` проверяет, есть ли `prototype` конструктора в цепочке прототипов объекта. Работает только для объектов, зато отличает массивы, даты и классы:

```js
[] instanceof Array;        // true
[] instanceof Object;       // true (Array наследуется от Object)
new Date() instanceof Date; // true
42 instanceof Number;       // false — примитив, не объект

class Dog {}
const rex = new Dog();
rex instanceof Dog;    // true
```

**Правило:** `typeof` — для примитивов и проверки `"function"`/`"undefined"`. `instanceof` — чтобы отличить массив/дату/класс от обычного объекта. Для массива вместо `instanceof Array` лучше `Array.isArray(value)` — он не ломается между разными `iframe`/realms.
