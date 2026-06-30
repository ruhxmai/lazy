---
id: css-animations
category: Frontend
difficulty: junior
daily: true
---

# В чём разница между CSS `transition` и `animation`?

## Ответ

**`transition`** — плавный переход между **двумя** состояниями. Запускается при изменении CSS-свойства (например, по `:hover` или добавлении класса).

**`animation`** — полноценная анимация через `@keyframes`. Можно задать несколько промежуточных шагов, зациклить, запустить без действий пользователя.

```css
/* transition: реагирует на смену состояния */
.button {
  background: blue;
  transition: background 0.3s ease, transform 0.2s;
}
.button:hover {
  background: red;
  transform: scale(1.05);
}

/* animation: управляется через @keyframes */
@keyframes spin {
  from { transform: rotate(0deg); }
  to   { transform: rotate(360deg); }
}

.loader {
  animation: spin 1s linear infinite;
}

/* Несколько шагов */
@keyframes pulse {
  0%   { opacity: 1; }
  50%  { opacity: 0.3; }
  100% { opacity: 1; }
}
```

| | `transition` | `animation` |
|---|---|---|
| Шаги | 2 (from → to) | Любое кол-во |
| Запуск | При изменении свойства | Автоматически |
| Повтор | Нет | `iteration-count: infinite` |
