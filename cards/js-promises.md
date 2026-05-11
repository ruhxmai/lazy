---
id: js-promises
category: Frontend
daily: true
---

# Что такое Promise и чем async/await отличается от .then()?

## Ответ

`Promise` — объект, представляющий результат асинхронной операции: `pending` → `fulfilled` или `rejected`.

```js
// .then() — цепочка колбэков
fetch('/api/data')
  .then(res => res.json())
  .then(data => console.log(data))
  .catch(err => console.error(err));

// async/await — тот же Promise, но читается как синхронный код
async function loadData() {
  try {
    const res = await fetch('/api/data');
    const data = await res.json();
    console.log(data);
  } catch (err) {
    console.error(err);
  }
}
```

`async/await` — синтаксический сахар над Promise. Делает код линейным и удобным для отладки.
