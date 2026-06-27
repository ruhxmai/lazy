---
id: css-animations
category: Frontend
daily: true
---
# Как сделать CSS-анимацию?
## Ответ
Два инструмента: `transition` для простых переходов и `@keyframes` для сложных анимаций.

**transition** — плавный переход при изменении свойства:
```css
.btn {
  background: blue;
  transition: background 0.3s ease;
}
.btn:hover { background: red; }
```

**@keyframes** — покадровая анимация:
```css
@keyframes pulse {
  0%   { transform: scale(1); }
  50%  { transform: scale(1.1); }
  100% { transform: scale(1); }
}
.icon {
  animation: pulse 1s infinite ease-in-out;
}
```

Синтаксис `animation`: `name duration timing-function delay iteration-count`.
