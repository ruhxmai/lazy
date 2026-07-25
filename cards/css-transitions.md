---
id: css-transitions
category: Frontend
daily: true
---

# Чем CSS-transition отличается от animation?

## Ответ

**Transition** — плавный переход **между двумя состояниями** свойства (например, при `:hover` или изменении класса). Требует триггера — сам по себе не запускается.

```css
.button {
  background: royalblue;
  transition: background 0.3s ease, transform 0.2s;
}
.button:hover {
  background: darkblue;
  transform: scale(1.05);
}
```

**Animation** (через `@keyframes`) описывает несколько промежуточных состояний и может идти **бесконечно**, без внешнего триггера.

```css
@keyframes pulse {
  0%   { opacity: 1; }
  50%  { opacity: 0.4; }
  100% { opacity: 1; }
}
.loader {
  animation: pulse 1.5s ease-in-out infinite;
}
```

| | transition | animation |
|---|---|---|
| Точки перехода | 2 (from → to) | сколько угодно (`@keyframes`) |
| Нужен триггер | да (`:hover`, JS, класс) | нет |
| Повтор/цикл | нет | `animation-iteration-count: infinite` |

Совет по производительности: анимировать лучше `transform` и `opacity` — они не вызывают reflow, в отличие от `width`/`top`/`margin`.
