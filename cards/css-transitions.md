---
id: css-transitions
category: Frontend
difficulty: junior
daily: true
---

# Как работает CSS transition?

## Ответ

`transition` плавно анимирует изменение CSS-свойства между двумя значениями, когда значение меняется (например, при `:hover` или смене класса через JS).

```css
.button {
  background: royalblue;
  transition: background 0.3s ease-in-out;
}

.button:hover {
  background: darkblue;
}
```

**Основные параметры (`transition-property | duration | timing-function | delay`):**
- `property` — какое свойство анимировать (`all` — все сразу, но дороже по производительности)
- `duration` — сколько длится анимация
- `timing-function` — кривая скорости (`ease`, `linear`, `ease-in-out`, `cubic-bezier(...)`)
- `delay` — задержка перед стартом

**Важно:** transition сработает только при **изменении значения свойства** — само по себе оно не запускает анимацию при загрузке страницы (для этого нужен `@keyframes` + `animation`).

Для производительности лучше анимировать `transform` и `opacity` — они не вызывают reflow.
