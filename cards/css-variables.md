---
id: css-variables
category: Frontend
daily: true
---
# Что такое CSS-переменные и как их использовать?
## Ответ
CSS-переменные (custom properties) позволяют хранить значения для повторного использования в стилях. Объявляются через `--name`, читаются через `var(--name)`.

```css
/* Глобальные переменные — обычно в :root */
:root {
  --color-primary: #3b82f6;
  --spacing-md: 16px;
  --border-radius: 8px;
}

.button {
  background: var(--color-primary);
  padding: var(--spacing-md);
  border-radius: var(--border-radius);
}

/* Переопределение в контексте (тема) */
.dark {
  --color-primary: #60a5fa;
}
```

Переменные наследуются и каскадируются как обычные CSS-свойства. Можно задавать fallback: `var(--color, #000)`.
