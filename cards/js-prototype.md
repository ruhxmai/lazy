---
id: js-prototype
category: JavaScript
daily: true
---
# Что такое цепочка прототипов в JavaScript?

## Ответ

В JavaScript каждый объект имеет скрытое свойство `[[Prototype]]`, которое ссылается на другой объект (или `null`). Это **прототипная цепочка**: при обращении к свойству JS ищет его сначала в самом объекте, затем поднимается вверх по цепочке.

```js
const animal = { breathes: true };
const dog = Object.create(animal);
dog.bark = function() { return 'Woof!'; };

console.log(dog.breathes); // true — взято из прототипа
console.log(dog.hasOwnProperty('breathes')); // false
```

- `Object.getPrototypeOf(obj)` — правильный способ получить прототип
- `__proto__` — устаревший, использовать не рекомендуется
- Конец цепочки: `Object.prototype` → `null`
- `class` в ES6 — синтаксический сахар над прототипным наследованием
