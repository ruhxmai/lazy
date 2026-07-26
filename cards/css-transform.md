---
id: css-transform
category: Frontend
difficulty: junior
daily: true
---

# Что делает CSS-свойство `transform`?

## Ответ

`transform` изменяет **визуальное представление** элемента (позицию, размер, поворот) **без влияния на поток документа** — соседние элементы не сдвигаются.

```css
.box {
  transform: translateX(20px) rotate(15deg) scale(1.2);
}
```

Основные функции:

- `translate(x, y)` — сдвиг
- `rotate(deg)` — поворот
- `scale(x, y)` — масштабирование
- `skew(x, y)` — наклон

```css
.card:hover {
  transform: translateY(-4px) scale(1.03);
  transition: transform 0.2s ease;
}
```

Важно: `transform` создаёт новый **stacking context** и часто ускоряется через GPU — поэтому анимировать `transform`/`opacity` предпочтительнее, чем `top`/`left`/`width` (это вызывает layout/reflow).
