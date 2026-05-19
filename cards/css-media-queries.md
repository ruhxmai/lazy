---
id: css-media-queries
category: Frontend
daily: true
---
# Что такое media queries и как работает подход mobile-first?

## Ответ
Media queries применяют CSS-стили в зависимости от ширины экрана или других характеристик устройства.

**Mobile-first** — пишем базовые стили для мобильных, затем переопределяем через `min-width`.

```css
/* базовые стили — мобильные */
.container {
  flex-direction: column;
}

/* планшеты (768px+) */
@media (min-width: 768px) {
  .container {
    flex-direction: row;
  }
}

/* десктоп (1200px+) */
@media (min-width: 1200px) {
  .container {
    max-width: 1200px;
  }
}
```

`min-width` — mobile-first. `max-width` — desktop-first.
