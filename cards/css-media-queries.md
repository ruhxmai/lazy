---
id: css-media-queries
category: Frontend
difficulty: junior
daily: true
---

# Что такое CSS Media Queries и как сделать адаптивный дизайн?

## Ответ

Media Queries позволяют применять CSS-правила **только при определённых условиях** (ширина экрана, ориентация устройства и т.д.).

```css
/* Mobile-first: стили по умолчанию — для мобильных */
.container {
  width: 100%;
  padding: 1rem;
}

/* Tablet: 768px и шире */
@media (min-width: 768px) {
  .container {
    max-width: 720px;
    margin: 0 auto;
  }
}

/* Desktop: 1024px и шире */
@media (min-width: 1024px) {
  .container {
    max-width: 960px;
  }
}
```

**Mobile-first** — рекомендуемый подход: пишешь стили для маленьких экранов, затем расширяешь через `min-width`.

Стандартные breakpoints:
- `480px` — мобильный landscape
- `768px` — планшет
- `1024px` — десктоп

> Противоположный подход — Desktop-first — использует `max-width`. Оба рабочие, но mobile-first считается лучшей практикой.
