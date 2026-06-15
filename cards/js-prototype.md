---
id: js-prototype
category: JavaScript
daily: true
---
# Что такое цепочка прототипов в JavaScript?
## Ответ
Каждый объект в JS имеет скрытое свойство `[[Prototype]]` (доступно через `__proto__`), указывающее на другой объект-прототип. Поиск свойства идёт вверх по цепочке до `null`.

```js
const animal = { breathes: true };
const dog = Object.create(animal);
dog.barks = true;

console.log(dog.breathes); // true (из прототипа)
console.log(dog.hasOwnProperty('breathes')); // false
```

Классы в JS — это синтаксический сахар над прототипами. `Dog.prototype.__proto__ === Animal.prototype`.
