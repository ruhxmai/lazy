---
id: css-variables
category: Frontend
difficulty: junior
daily: true
---

# Что такое CSS-переменные (custom properties)?

## Ответ

CSS-переменные позволяют хранить значения и переиспользовать их по всему стилю. Объявляются через `--`, используются через `var()`.

```css
:root {
  --color-primary: #3498db;
  --spacing-md: 16px;
  --font-size-base: 1rem;
}

.button {
  background: var(--color-primary);
  padding: var(--spacing-md);
  font-size: var(--font-size-base);
}

/* Переопределение для темы */
.dark-theme {
  --color-primary: #2980b9;
}
```

- Каскадируются как обычные CSS-свойства
- Доступны в JS: `getComputedStyle(el).getPropertyValue('--color-primary')`
- Поддерживают запасное значение: `var(--color, red)`
- Отличие от SASS-переменных: обновляются в реальном времени (runtime)
