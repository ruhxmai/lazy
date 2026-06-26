---
id: js-spread-rest
category: JavaScript
daily: true
---
# Чем отличается spread от rest в JavaScript?
## Ответ
**Rest** (`...`) собирает аргументы в массив — используется в параметрах функции.
**Spread** (`...`) разворачивает массив/объект в отдельные элементы — используется в вызовах.

```js
// rest — сбор аргументов
function sum(...nums) {
  return nums.reduce((a, b) => a + b, 0);
}
sum(1, 2, 3); // 6

// spread — разворот массива
const a = [1, 2];
const b = [0, ...a, 3]; // [0, 1, 2, 3]

// spread — копирование объекта
const obj1 = { x: 1 };
const obj2 = { ...obj1, y: 2 }; // { x: 1, y: 2 }
```

Правило: rest стоит **последним** в параметрах, spread можно использовать везде.
