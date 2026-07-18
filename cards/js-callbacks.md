---
id: js-callbacks
category: Frontend
difficulty: junior
daily: true
---

# Что такое callback-функция и в чём проблема callback hell?

## Ответ

**Callback** — функция, переданная в другую функцию как аргумент и вызываемая позже, когда работа будет готова (например, после ответа сервера или таймера).

```js
function loadUser(id, callback) {
  setTimeout(() => {
    callback({ id, name: "Alice" });
  }, 1000);
}

loadUser(1, (user) => console.log(user.name));
```

**Callback hell** — когда колбэки вложены друг в друга ради последовательных асинхронных шагов. Код превращается в «пирамиду» и трудно читается:

```js
loadUser(1, (user) => {
  loadPosts(user.id, (posts) => {
    loadComments(posts[0].id, (comments) => {
      console.log(comments); // и так далее вглубь
    });
  });
});
```

Решается через **Promise** и `async/await` — они разворачивают вложенность в плоскую линейную последовательность.
