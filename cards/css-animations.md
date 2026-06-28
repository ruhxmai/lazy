---
id: css-animations
category: Frontend
daily: true
---
# Чем отличаются CSS transition и animation?
## Ответ
**Transition** — плавный переход между двумя состояниями при изменении свойства (нужен внешний триггер, например `:hover`).

**Animation** — многошаговая анимация с ключевыми кадрами (`@keyframes`), может запускаться автоматически.

```css
/* Transition — срабатывает при :hover */
.btn {
  background: blue;
  transition: background 0.3s ease;
}
.btn:hover {
  background: red;
}

/* Animation — запускается сама */
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

| Свойство | Transition | Animation |
|---|---|---|
| Триггер | внешний (hover, class) | автоматически |
| Шаги | 2 (начало → конец) | неограниченно |
| Повтор | нет | `infinite` |
