---
id: css-animations
category: Frontend
difficulty: junior
daily: true
---

# Чем `transition` отличается от `animation` в CSS?

## Ответ

**`transition`** — плавная смена одного состояния в другое (при hover, focus, классе и т.д.).

```css
.btn {
  background: blue;
  transition: background 0.3s ease, transform 0.2s;
}

.btn:hover {
  background: red;
  transform: scale(1.05);
}
```

**`animation` + `@keyframes`** — независимая анимация по ключевым кадрам, запускается автоматически.

```css
@keyframes spin {
  from { transform: rotate(0deg); }
  to   { transform: rotate(360deg); }
}

.loader {
  animation: spin 1s linear infinite;
}
```

**Ключевые свойства animation:**
- `animation-duration` — длительность
- `animation-delay` — задержка перед стартом
- `animation-iteration-count` — кол-во повторений (`infinite`)
- `animation-timing-function` — `ease`, `linear`, `ease-in-out`
- `animation-fill-mode` — `forwards` сохраняет конечное состояние
