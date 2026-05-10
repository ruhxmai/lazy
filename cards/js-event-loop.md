---
id: js-event-loop
category: Frontend
difficulty: junior
daily: true
---

# Что такое Event Loop?

## Ответ

Механизм, который делает JavaScript асинхронным, несмотря на то что JS — однопоточный.

**Порядок выполнения:**
1. **Call Stack** — синхронный код выполняется сразу
2. **Microtasks** — `Promise.then`, `queueMicrotask` (приоритет выше)
3. **Macrotasks** — `setTimeout`, `setInterval`, события

```js
console.log('1');
setTimeout(() => console.log('3'), 0);
Promise.resolve().then(() => console.log('2'));
// Вывод: 1 → 2 → 3
```
