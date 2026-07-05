---
id: css-animations
category: Frontend
daily: true
---
# Чем отличается `transition` от `animation` в CSS?

## Ответ

`transition` описывает **плавный переход между двумя состояниями** и запускается только по триггеру (`:hover`, изменение класса, инлайн-стиля).

```css
.button {
  background: blue;
  transition: background 0.3s ease;
}
.button:hover {
  background: darkblue;
}
```

`animation` работает через `@keyframes` — можно задать сколько угодно промежуточных состояний, зациклить и запустить **без внешнего триггера**, сразу при загрузке.

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
| Нужен триггер | Да | Нет |
| Промежуточные шаги | Только начало/конец | Любое число (`@keyframes`) |
| Зацикливание | Нет | `infinite`, `iteration-count` |
| Управление паузой | Нет | `animation-play-state` |
