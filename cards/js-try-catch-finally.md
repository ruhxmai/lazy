---
id: js-try-catch-finally
category: Frontend
difficulty: junior
daily: true
---

# Как работают try/catch/finally и когда выполняется finally?

## Ответ

`try` — код, который может выбросить ошибку. `catch` — обработка ошибки. `finally` — выполняется **всегда**, независимо от того, была ошибка или был `return`.

```js
function readValue() {
  try {
    throw new Error('boom');
  } catch (err) {
    console.log('caught:', err.message);
    return 'from catch';
  } finally {
    console.log('cleanup');
  }
}

readValue();
// caught: boom
// cleanup
// -> 'from catch'
```

`finally` выполнится даже при `return` внутри `try` или `catch` — это удобно для очистки ресурсов (закрыть соединение, скрыть лоадер), независимо от результата.

**Важная ловушка:** `return` внутри `finally` перезапишет любой `return`/`throw` из `try`/`catch` — так писать не стоит, это делает поведение функции неочевидным:

```js
function risky() {
  try {
    return 1;
  } finally {
    return 2; // ⚠️ функция вернёт 2, а не 1
  }
}
```