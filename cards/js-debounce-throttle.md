---
id: js-debounce-throttle
category: Frontend
difficulty: junior
daily: true
---

# В чём разница между debounce и throttle?

## Ответ

Оба ограничивают частоту вызова функции, но по-разному.

**Debounce** — вызывает функцию только после того, как события **перестали** приходить (пауза в N мс):

```js
function debounce(fn, delay) {
  let timer;
  return (...args) => {
    clearTimeout(timer);
    timer = setTimeout(() => fn(...args), delay);
  };
}

const onSearch = debounce((query) => fetchResults(query), 300);
input.addEventListener('input', (e) => onSearch(e.target.value));
// Запрос уйдёт только когда пользователь перестал печатать
```

**Throttle** — вызывает функцию не чаще, чем раз в N мс, независимо от того, сколько событий пришло:

```js
function throttle(fn, delay) {
  let last = 0;
  return (...args) => {
    const now = Date.now();
    if (now - last >= delay) {
      last = now;
      fn(...args);
    }
  };
}

const onScroll = throttle(() => updatePosition(), 200);
window.addEventListener('scroll', onScroll);
// Обработчик сработает максимум раз в 200мс во время скролла
```

**Правило:** debounce для поиска/автосохранения (ждём паузу), throttle для scroll/resize (нужен регулярный отклик).
