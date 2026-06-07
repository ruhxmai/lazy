---
id: js-prototype
category: JavaScript
difficulty: junior
daily: true
---

# Что такое цепочка прототипов в JavaScript?

## Ответ

Каждый объект в JS имеет скрытое свойство `[[Prototype]]` (доступно через `__proto__`), которое указывает на другой объект — его прототип. При обращении к свойству JS ищет его сначала в самом объекте, затем поднимается по цепочке до `null`.

```js
const animal = { speak() { return "..."; } };
const dog = Object.create(animal);
dog.name = "Rex";

console.log(dog.speak());              // "..." — найдено в прототипе
console.log(dog.hasOwnProperty("name"));  // true
console.log(dog.hasOwnProperty("speak")); // false
```

- `Object.create(proto)` — создаёт объект с указанным прототипом
- `instanceof` проверяет цепочку прототипов
- В конце цепочки всегда `Object.prototype`, затем `null`
- Функции-конструкторы используют `prototype` для настройки цепочки
