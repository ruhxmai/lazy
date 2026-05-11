---
id: css-flexbox
category: Frontend
daily: true
---

# Как работает Flexbox и что делает justify-content?

## Ответ

Flexbox — модель раскладки для выравнивания элементов вдоль одной оси (строки или колонки).

```css
.container {
  display: flex;
  justify-content: space-between; /* распределение по главной оси */
  align-items: center;            /* выравнивание по поперечной оси */
}
```

`justify-content` управляет **главной осью** (по умолчанию — горизонталь), `align-items` — **поперечной осью** (вертикаль). Значения: `flex-start`, `flex-end`, `center`, `space-between`, `space-around`.
