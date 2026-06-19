---
id: css-variables
category: Frontend
daily: true
---
# Что такое CSS Custom Properties (переменные)?
## Ответ
CSS-переменные хранят значения и позволяют переиспользовать их в стилях. Объявляются через `--имя`, используются через `var()`.

```css
:root {
  --primary: #3498db;
  --radius: 8px;
}

.button {
  background: var(--primary);
  border-radius: var(--radius);
}

/* Переопределение в компоненте */
.button--danger {
  --primary: #e74c3c;
}
```

Отличие от переменных Sass: CSS-переменные **живые** — их можно читать и менять через JavaScript:

```javascript
document.documentElement.style.setProperty('--primary', '#ff0');
```
