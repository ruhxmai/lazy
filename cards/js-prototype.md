---
id: js-prototype
category: JavaScript
daily: true
---
# Что такое цепочка прототипов в JavaScript?
## Ответ
Каждый объект в JS имеет скрытую ссылку `[[Prototype]]` на другой объект (прототип). Если свойство не найдено в самом объекте, поиск идёт вверх по цепочке прототипов до `null`.

```js
const animal = { breathes: true };
const dog = Object.create(animal);
dog.barks = true;

console.log(dog.breathes);                   // true — взято из прототипа
console.log(dog.hasOwnProperty('breathes')); // false
```

Цепочка: `dog` → `animal` → `Object.prototype` → `null`
