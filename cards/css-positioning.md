---
id: css-positioning
category: Frontend
daily: true
---
# Чем отличаются position: relative, absolute, fixed и sticky?
## Ответ
- **static** — по умолчанию, в обычном потоке, `top/left` не работают
- **relative** — остаётся в потоке, смещается визуально относительно себя
- **absolute** — вырывается из потока, позиционируется по ближайшему предку с `position ≠ static`
- **fixed** — вырывается из потока, позиционируется по viewport (остаётся при скролле)
- **sticky** — `relative` до порога прокрутки, затем «приклеивается» как `fixed`

```css
.parent { position: relative; }

.tooltip {
  position: absolute;
  top: 0;
  right: 0; /* угол родителя */
}

.header {
  position: sticky;
  top: 0; /* приклеится при скролле */
}

.modal {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```
