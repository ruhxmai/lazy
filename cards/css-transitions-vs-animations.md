---
id: css-transitions-vs-animations
category: Frontend
difficulty: junior
daily: true
---

# Чем CSS `transition` отличается от `animation`?

## Ответ

**`transition`** — плавный переход между **двумя состояниями** свойства, запускается внешним триггером (`:hover`, изменение класса через JS). Не может выполняться сама по себе и не зацикливается.

```css
.button {
  background: blue;
  transition: background 0.3s ease;
}
.button:hover {
  background: darkblue; /* transition сработает при наведении */
}
```

**`animation`** — самостоятельная последовательность **из нескольких кадров** (`@keyframes`), может запускаться сразу при загрузке, повторяться (`infinite`) и не требует внешнего триггера.

```css
@keyframes pulse {
  0%   { transform: scale(1); }
  50%  { transform: scale(1.1); }
  100% { transform: scale(1); }
}

.badge {
  animation: pulse 1.5s ease-in-out infinite;
}
```

| | `transition` | `animation` |
|---|---|---|
| Нужен триггер (`:hover`, класс) | Да | Нет, может стартовать сама |
| Промежуточные кадры (`@keyframes`) | Нет, только from→to | Да, любое количество |
| Зацикливание | Нет | Да (`animation-iteration-count`) |
| Управление паузой | Ограничено | `animation-play-state: paused` |

**Правило:** для простых состояний по действию пользователя — `transition`; для сложных, самозапускающихся или зацикленных эффектов — `animation`.
