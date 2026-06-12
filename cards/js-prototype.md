---
id: js-prototype
category: JavaScript
daily: true
---
# Что такое прототип в JavaScript и как работает цепочка прототипов?
## Ответ
Каждый объект в JS имеет скрытое свойство `[[Prototype]]`, указывающее на другой объект. При обращении к свойству JS ищет его сначала в самом объекте, затем поднимается по цепочке прототипов до `null`.

```js
const animal = { breathes: true };
const dog = Object.create(animal);
dog.barks = true;

console.log(dog.breathes);              // true — нашёл у animal
console.log(dog.hasOwnProperty('breathes')); // false
console.log(Object.getPrototypeOf(dog) === animal); // true
```

`__proto__` — устаревший способ доступа к прототипу, рекомендуется `Object.getPrototypeOf(obj)` / `Object.setPrototypeOf(obj, proto)`.
