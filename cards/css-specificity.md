---
id: css-specificity
category: Frontend
difficulty: junior
daily: true
---

# Как считается специфичность (specificity) CSS-селекторов?

## Ответ

Специфичность определяет, какое правило "победит" при конфликте. Считается как вес из четырёх категорий: `(inline, id, class/attr/pseudo-class, tag)`.

```css
/* tag: 0-0-0-1 */
p { color: black; }

/* class: 0-0-1-0 — побеждает */
.text { color: blue; }

/* id: 0-1-0-0 — побеждает всё выше */
#main { color: green; }

/* inline style="color: red" — 1-0-0-0, побеждает всё, кроме !important */
```

Правила сравнения:
- Больше `id` побеждает, даже если классов и тегов больше
- При равной специфичности побеждает правило, объявленное **позже**
- `!important` перебивает специфичность, но ломает предсказуемость — избегайте

```css
/* Специфичность 0-1-1-1 vs 0-0-2-0 → id побеждает */
#nav .item.active { color: red; }   /* 0-1-1-1 */
.item.disabled.hidden { color: gray; } /* 0-0-3-0, но проигрывает — тут id важнее */
```
