---
id: js-prototype
category: Frontend
difficulty: junior
daily: true
---

# Что такое цепочка прототипов в JavaScript?

## Ответ

Каждый объект в JS имеет скрытое свойство `[[Prototype]]`, которое ссылается на другой объект — его прототип. При обращении к свойству JS сначала ищет его в самом объекте, затем поднимается по цепочке прототипов вверх.

```js
const animal = {
  speak() {
    return 'Sound';
  }
};

const dog = Object.create(animal);
dog.name = 'Rex';

console.log(dog.speak()); // 'Sound' — взято из прототипа
console.log(dog.hasOwnProperty('name'));  // true
console.log(dog.hasOwnProperty('speak')); // false
```

- `Object.create(proto)` создаёт объект с заданным прототипом
- `Object.getPrototypeOf(obj)` — правильный способ получить прототип
- Цепочка заканчивается на `Object.prototype`, затем `null`
- Классы в JS — синтаксический сахар над прототипным наследованием
