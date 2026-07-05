---
id: js-event-delegation
category: Frontend
daily: true
---
# Что такое делегирование событий (event delegation) в JavaScript?

## Ответ

Вместо того чтобы вешать обработчик на каждый дочерний элемент, вешаем **один** обработчик на общего родителя и используем всплытие событий (`bubbling`). Внутри обработчика смотрим, на каком именно элементе произошло событие, через `event.target`.

```js
// Плохо: обработчик на каждый li, не работает для новых элементов
document.querySelectorAll('li').forEach(li => {
  li.addEventListener('click', handleClick);
});

// Хорошо: один обработчик на родителе
document.querySelector('ul').addEventListener('click', (event) => {
  const item = event.target.closest('li');
  if (!item) return;
  console.log('Клик по:', item.textContent);
});
```

**Плюсы:**
- Один обработчик вместо N — меньше памяти
- Работает для элементов, добавленных динамически после навешивания обработчика
- Не нужно вручную снимать обработчики при удалении элементов

Используется в React (`SyntheticEvent`), в списках, таблицах, меню.
