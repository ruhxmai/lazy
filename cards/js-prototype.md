---
id: js-prototype
category: JavaScript
daily: true
---
# Что такое цепочка прототипов в JavaScript?

## Ответ

Каждый объект в JS имеет скрытое свойство `[[Prototype]]` (доступно через `__proto__` или `Object.getPrototypeOf()`). Когда свойство не найдено в самом объекте, поиск продолжается вверх по цепочке прототипов вплоть до `null`.

```js
function Animal(name) {
  this.name = name;
}
Animal.prototype.speak = function () {
  return `${this.name} говорит`;
};

const dog = new Animal('Rex');
console.log(dog.speak()); // 'Rex говорит'
// dog -> Animal.prototype -> Object.prototype -> null
```

Современный синтаксис `class` — это синтаксический сахар поверх прототипов, механизм остаётся тем же.
