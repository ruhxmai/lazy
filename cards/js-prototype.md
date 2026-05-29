---
id: js-prototype
category: JavaScript
daily: true
---
# Что такое цепочка прототипов (prototype chain) в JavaScript?

## Ответ

Каждый объект в JS имеет скрытое свойство `[[Prototype]]`, которое ссылается на другой объект (или `null`). При обращении к свойству JS ищет его сначала в самом объекте, затем поднимается по цепочке прототипов.

```js
const animal = { breathes: true };
const dog = Object.create(animal);
dog.name = 'Rex';

console.log(dog.name);     // 'Rex'  — собственное свойство
console.log(dog.breathes); // true   — из прототипа
console.log(Object.getPrototypeOf(dog) === animal); // true
```

`Object.create(proto)` создаёт объект с явно заданным прототипом. Классы (`class`/`extends`) — это синтаксический сахар над этим же механизмом.
