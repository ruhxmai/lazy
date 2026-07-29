---
id: css-transform
category: Frontend
daily: true
---

# Что делает CSS-свойство transform и почему оно не влияет на layout?

## Ответ

`transform` изменяет визуальное положение/размер/поворот элемента, **не затрагивая поток документа** — соседние элементы не сдвигаются, `getBoundingClientRect` меняется, но `offsetTop/offsetLeft` — нет.

```css
.box {
  transform: translate(20px, 10px) rotate(45deg) scale(1.2);
}
```

**Основные функции:**

```css
transform: translateX(50px);   /* сдвиг по X */
transform: translateY(-10px);  /* сдвиг по Y */
transform: scale(1.5);         /* увеличение в 1.5 раза */
transform: rotate(90deg);      /* поворот */
transform: skew(10deg, 0deg);  /* наклон */
```

Порядок функций в списке важен — `translate(50px) rotate(45deg)` даёт другой результат, чем `rotate(45deg) translate(50px)`, потому что каждая следующая трансформация применяется в уже повёрнутой системе координат.

**Почему это быстрее, чем менять `top/left/width`:**

Изменение `top`/`left`/`width`/`height` запускает **layout (reflow)** — браузер пересчитывает позиции всех элементов. `transform` (как и `opacity`) обрабатывается на этапе **composite** и может ускоряться GPU, поэтому именно их используют для плавных анимаций.

```css
/* Медленно: триггерит layout на каждый кадр */
.slow { left: 100px; transition: left 0.3s; }

/* Быстро: только composite */
.fast { transform: translateX(100px); transition: transform 0.3s; }
```

`transform-origin` задаёт точку, относительно которой применяется трансформация (по умолчанию — центр элемента, `50% 50%`).
