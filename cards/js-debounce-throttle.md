---
id: js-debounce-throttle
category: Frontend
daily: true
---
# В чём разница между debounce и throttle?

## Ответ

Оба приёма ограничивают, как часто вызывается функция при частых событиях (скролл, resize, ввод текста), но по-разному.

**Debounce** — откладывает вызов, пока события не прекратятся на заданное время. Если событие повторилось раньше — таймер сбрасывается.

```js
function debounce(fn, delay) {
  let timer;
  return (...args) => {
    clearTimeout(timer);
    timer = setTimeout(() => fn(...args), delay);
  };
}

const search = debounce((q) => fetchResults(q), 300);
input.addEventListener('input', (e) => search(e.target.value));
// fetchResults вызовется только через 300мс ПОСЛЕ того, как пользователь перестал печатать
```

**Throttle** — гарантирует вызов не чаще, чем раз в заданный интервал, даже если события идут непрерывно.

```js
function throttle(fn, interval) {
  let last = 0;
  return (...args) => {
    const now = Date.now();
    if (now - last >= interval) {
      last = now;
      fn(...args);
    }
  };
}

window.addEventListener('scroll', throttle(() => checkPosition(), 200));
// checkPosition вызывается максимум раз в 200мс, пока идёт скролл
```

**Когда что использовать:** debounce — для поиска, автосохранения, валидации формы (важен только финальный результат). Throttle — для скролла, resize, drag (важно регулярно реагировать, но не на каждый пиксель).
