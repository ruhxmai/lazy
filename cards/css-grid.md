---
id: css-grid
category: Frontend
difficulty: junior
daily: true
---

# Как создать сетку с CSS Grid?

## Ответ

CSS Grid — двумерная система раскладки (строки + столбцы), в отличие от Flexbox (одна ось).

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr; /* 3 равных столбца */
  grid-template-rows: auto;
  gap: 16px;
}

/* Растянуть элемент на 2 столбца */
.item-wide {
  grid-column: span 2;
}
```

- `fr` — доля свободного пространства
- `gap` — отступы между ячейками
- `grid-template-areas` позволяет именовать зоны сетки
