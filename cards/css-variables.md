---
id: css-variables
category: Frontend
daily: true
---
# Что такое CSS Custom Properties (переменные)?
## Ответ
CSS-переменные (custom properties) хранят значения для повторного использования. Объявляются через `--имя`, используются через `var()`.

```css
/* Объявление глобальных переменных */
:root {
  --color-primary: #3498db;
  --spacing-md: 16px;
  --font-size-base: 1rem;
}

.button {
  background: var(--color-primary);
  padding: var(--spacing-md);
  /* Запасное значение, если переменная не определена */
  color: var(--text-color, #fff);
}

/* Переопределение в рамках компонента */
.card {
  --color-primary: #e74c3c;
}
```

Переменные каскадируются как обычные CSS-свойства и доступны в JavaScript:
```js
getComputedStyle(el).getPropertyValue('--color-primary');
el.style.setProperty('--color-primary', '#2ecc71');
```
