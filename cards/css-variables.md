---
id: css-variables
category: Frontend
difficulty: junior
daily: true
---

# Что такое CSS-переменные и как их использовать?

## Ответ

CSS custom properties (переменные) — именованные значения, которые можно переиспользовать в стилях. Объявляются через `--имя`, читаются через `var(--имя)`.

```css
/* Глобальное объявление в :root */
:root {
  --color-primary: #3b82f6;
  --color-text: #1a1a1a;
  --spacing-md: 16px;
  --radius: 8px;
}

/* Использование */
.button {
  background: var(--color-primary);
  color: #fff;
  padding: var(--spacing-md);
  border-radius: var(--radius);
}

/* Запасное значение (fallback) */
.card {
  color: var(--color-text, #333); /* если --color-text не задана — #333 */
}

/* Локальное переопределение (тема) */
[data-theme="dark"] {
  --color-primary: #60a5fa;
  --color-text: #f5f5f5;
}
```

Переменные **наследуются** по DOM и могут переопределяться в любом элементе — удобно для тем оформления.
