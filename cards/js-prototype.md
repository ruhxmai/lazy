---
id: js-prototype
category: Frontend
daily: true
---

# Что такое цепочка прототипов (prototype chain)?

## Ответ

Каждый объект в JS имеет скрытую ссылку `[[Prototype]]` на другой объект. Когда свойство не найдено на самом объекте — JS ищет его вверх по цепочке прототипов.

```js
const animal = { breathes: true };
const dog = Object.create(animal);
dog.bark = true;

console.log(dog.bark);             // true (собственное)
console.log(dog.breathes);         // true (из прототипа)
console.log(dog.__proto__ === animal); // true
```

Цепочка заканчивается на `Object.prototype`, у которого `[[Prototype]] = null`. Если свойство не найдено нигде — возвращается `undefined`.
