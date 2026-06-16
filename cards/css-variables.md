---
id: css-variables
category: Frontend
daily: true
---
# Что такое CSS-переменные (custom properties)?

## Ответ

CSS custom properties — переменные в CSS, объявляемые с префиксом `--`. Позволяют хранить значения и переиспользовать их, упрощая темизацию и поддержку кода.

- Объявляются в `:root` для глобального доступа
- Читаются через `var(--name, fallback)`
- Наследуются вниз по DOM
- Могут переопределяться в локальных селекторах (например для тёмной темы)

```css
:root {
  --primary: #3498db;
  --radius: 8px;
}

.button {
  background: var(--primary);
  border-radius: var(--radius);
}

.dark {
  --primary: #1a5276; /* переопределение для тёмной темы */
}
```
