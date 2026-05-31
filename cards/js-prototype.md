---
id: js-prototype
category: JavaScript
daily: true
---
# Что такое цепочка прототипов в JavaScript?
## Ответ
Каждый объект в JS имеет внутреннее свойство `[[Prototype]]`, ссылающееся на другой объект (или `null`). При обращении к свойству JS сначала ищет его в самом объекте, затем поднимается по цепочке прототипов вверх.

```js
const animal = { breathes: true };
const dog = Object.create(animal);
dog.bark = () => 'woof';

console.log(dog.breathes); // true — найдено в прототипе
console.log(dog.hasOwnProperty('breathes')); // false

Object.getPrototypeOf(dog) === animal; // true
```

Классы в JS — синтаксический сахар над той же прототипной моделью.
