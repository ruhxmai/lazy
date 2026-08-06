---
id: css-transition
category: Frontend
daily: true
---

# Чем CSS transition отличается от animation?

## Ответ

`transition` плавно анимирует изменение свойства между двумя состояниями и запускается только по событию (например, `:hover`, добавление класса).

```css
.button {
  background: blue;
  transition: background 0.3s ease;
}
.button:hover {
  background: red;
}
```

`animation` работает независимо от событий, описывается через `@keyframes` и может зацикливаться сама по себе.

```css
@keyframes pulse {
  0%   { transform: scale(1); }
  50%  { transform: scale(1.1); }
  100% { transform: scale(1); }
}
.loader {
  animation: pulse 1s ease-in-out infinite;
}
```

| | `transition` | `animation` |
|---|---|---|
| Триггер | Нужно событие (hover, класс, JS) | Запускается сама при применении |
| Промежуточные шаги | Только начало → конец | Любое кол-во через `@keyframes` |
| Зацикливание | Нет | Да, через `infinite` |
| Управление паузой | Нет | Да, `animation-play-state` |
