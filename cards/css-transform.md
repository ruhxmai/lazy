---
id: css-transform
category: Frontend
daily: true
---

# Чем `transform` отличается от изменения `top`/`left`/`position`?

## Ответ

Оба способа двигают элемент, но по-разному влияют на браузерный рендеринг.

```css
/* Через layout-свойства — браузер пересчитывает поток документа */
.box-slow {
  position: relative;
  top: 50px;
  left: 20px;
}

/* Через transform — только композитинг на GPU */
.box-fast {
  transform: translate(20px, 50px);
}
```

| | `top`/`left` | `transform: translate()` |
|---|---|---|
| Этап рендеринга | Layout → Paint → Composite | Только Composite |
| Влияет на соседние элементы | Может (reflow) | Нет |
| Ускорение GPU | Нет | Да |
| Подходит для анимаций | Плохо (лаги, дёрганья) | Хорошо (60 fps) |

**Основные функции `transform`:**

```css
transform: translateX(10px);      /* сдвиг по X */
transform: scale(1.2);            /* масштаб 120% */
transform: rotate(45deg);         /* поворот */
transform: skew(10deg, 0deg);     /* наклон */
transform: translate(10px, 20px) rotate(5deg) scale(1.1); /* комбинация */
```

**Правило:** для анимаций позиции, масштаба и поворота всегда предпочитать `transform` (и `opacity`) — они не вызывают reflow и работают на композитном слое GPU.
