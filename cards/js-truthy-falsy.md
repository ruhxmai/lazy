---
id: js-truthy-falsy
category: Frontend
difficulty: junior
daily: true
---

# Какие значения в JavaScript считаются falsy?

## Ответ

Всего **6 falsy-значений**: `false`, `0` (и `-0`), `""` (пустая строка), `null`, `undefined`, `NaN`.

```js
if (false)     // не выполнится
if (0)         // не выполнится
if ('')        // не выполнится
if (null)      // не выполнится
if (undefined) // не выполнится
if (NaN)       // не выполнится

if ('0')       // выполнится! строка "0" — truthy
if ([])        // выполнится! пустой массив — truthy
if ({})        // выполнится! пустой объект — truthy
```

**Частая ловушка:** пустой массив и пустой объект — **truthy**, хотя интуитивно кажутся «пустыми» и falsy. Проверять пустой массив нужно через `arr.length === 0`, а не `if (!arr)`.

```js
const arr = [];
if (!arr) {
  console.log('пусто'); // не выполнится — arr truthy!
}
if (arr.length === 0) {
  console.log('пусто'); // правильная проверка
}
```
