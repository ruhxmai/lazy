---
id: js-prototype
category: JavaScript
daily: true
---
# Что такое цепочка прототипов в JavaScript?
## Ответ
Каждый объект в JS имеет скрытую ссылку `[[Prototype]]`. При обращении к свойству JS ищет его сначала в самом объекте, затем поднимается по цепочке прототипов до `Object.prototype`.

```js
const animal = { breathes: true };
const dog = Object.create(animal);
dog.barks = true;

console.log(dog.barks);    // true — собственное свойство
console.log(dog.breathes); // true — из прототипа
console.log(dog.hasOwnProperty('breathes')); // false

console.log(Object.getPrototypeOf(dog) === animal); // true
```

Цепочка заканчивается на `Object.prototype`, у которого `[[Prototype]] === null`.
