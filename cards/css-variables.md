---
id: css-variables
category: Frontend
daily: true
---
# Что такое CSS-переменные и как их использовать?
## Ответ
CSS-переменные (custom properties) объявляются через `--name` и применяются через `var(--name)`. Обычно объявляют в `:root`, чтобы переменная была глобальной.

```css
:root {
  --primary: #3b82f6;
  --spacing: 8px;
  --radius: 4px;
}

.button {
  background: var(--primary);
  padding: var(--spacing) calc(var(--spacing) * 2);
  border-radius: var(--radius);
}

/* Тёмная тема — просто переопределяем переменные */
[data-theme="dark"] {
  --primary: #60a5fa;
}
```

Переменные наследуются и каскадируются. Читать и менять их можно через JS:
```js
getComputedStyle(el).getPropertyValue('--primary');
el.style.setProperty('--primary', '#ff0000');
```
