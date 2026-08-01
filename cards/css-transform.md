---
id: css-transform
category: Frontend
daily: true
---

# Чем `transform` лучше `top`/`left` для анимации?

## Ответ

`transform` (translate, scale, rotate, skew) не влияет на **layout** страницы — браузер не пересчитывает позиции других элементов, а меняет только внешний вид уже отрисованного слоя. Это работает на GPU и не вызывает **reflow**.

```css
/* Плохо: меняет layout на каждом кадре (reflow + repaint) */
.box {
  position: absolute;
  transition: left 0.3s, top 0.3s;
}
.box:hover {
  left: 20px;
  top: 20px;
}

/* Хорошо: только composite-слой (GPU), без reflow */
.box {
  transition: transform 0.3s;
}
.box:hover {
  transform: translate(20px, 20px);
}
```

Основные функции `transform`:
- `translate(x, y)` — сдвиг
- `scale(x, y)` — масштаб
- `rotate(deg)` — поворот
- `skew(deg)` — наклон

Для плавных 60 FPS анимаций комбинируйте `transform` с `opacity` — это единственные свойства, которые браузер может анимировать, минуя пересчёт layout и paint.
