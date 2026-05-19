---
id: js-prototype
category: Frontend
daily: true
---
# Что такое цепочка прототипов в JavaScript?

## Ответ
Каждый объект в JS имеет скрытое свойство `[[Prototype]]`, ссылающееся на другой объект — прототип. При обращении к свойству JS ищет его сначала в самом объекте, затем поднимается по цепочке до `null`.

```js
const animal = { breathes: true };
const dog = Object.create(animal);
dog.barks = true;

console.log(dog.breathes);                   // true (из прототипа)
console.log(dog.hasOwnProperty('breathes')); // false
```

Цепочка: `dog → animal → Object.prototype → null`

`__proto__` — устаревший способ доступа к прототипу; современный: `Object.getPrototypeOf(obj)`.
