---
id: css-bem
category: Frontend
difficulty: junior
daily: true
---

# Что такое методология BEM в CSS?

## Ответ

**BEM** (Block, Element, Modifier) — соглашение об именовании CSS-классов, которое делает стили предсказуемыми и убирает конфликты специфичности.

```
.block {}
.block__element {}
.block__element--modifier {}
```

- **Block** — независимый компонент (`card`, `menu`)
- **Element** (`__`) — часть блока, не существует отдельно от него (`card__title`)
- **Modifier** (`--`) — вариант или состояние блока/элемента (`card--highlighted`)

```html
<div class="card card--highlighted">
  <h2 class="card__title">Заголовок</h2>
  <button class="card__button card__button--disabled">OK</button>
</div>
```

```css
.card { border: 1px solid #ddd; }
.card--highlighted { border-color: gold; }
.card__title { font-size: 20px; }
.card__button--disabled { opacity: 0.5; pointer-events: none; }
```

Плюсы: плоская специфичность (все селекторы — один класс), нет вложенных селекторов, легко понять структуру компонента по имени класса, не ломается при переносе элемента в другое место разметки.
