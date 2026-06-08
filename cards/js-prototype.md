---
id: js-prototype
category: Frontend
difficulty: junior
daily: true
---

# Что такое прототип в JavaScript?

## Ответ

Каждый объект в JS имеет скрытую ссылку `[[Prototype]]` на другой объект. Если свойство не найдено в самом объекте, поиск идёт вверх по **цепочке прототипов**.

```js
const animal = { breathes: true };
const dog = Object.create(animal);
dog.name = 'Rex';

console.log(dog.breathes);              // true (из прототипа)
console.log(dog.hasOwnProperty('name'));     // true
console.log(dog.hasOwnProperty('breathes')); // false
```

`Object.create(proto)` создаёт объект с указанным прототипом. Классы ES6 — это синтаксический сахар над прототипами: `class Dog extends Animal` под капотом настраивает цепочку прототипов.
