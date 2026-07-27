---
id: css-transform
category: Frontend
daily: true
---

# Что такое CSS transform и почему он лучше top/left для анимаций?

## Ответ

`transform` меняет положение, размер и поворот элемента, **не влияя на layout** документа:

```css
.box {
  transform: translate(20px, 10px) rotate(15deg) scale(1.2);
  transform-origin: center;
  transition: transform 0.3s ease;
}

.box:hover {
  transform: translateY(-4px) scale(1.05);
}
```

Основные функции: `translate()`, `rotate()`, `scale()`, `skew()` (и `*3d()`-варианты для 3D).

**Почему быстрее, чем анимировать `top`/`left`:**

| | `top` / `left` | `transform` |
|---|---|---|
| Что пересчитывает браузер | Layout → Paint → Composite | Только Composite |
| Нагрузка на CPU | Высокая (reflow всей страницы) | Низкая (работает на GPU) |
| Плавность на слабых устройствах | Может лагать | Обычно 60 fps |

Изменение `top`/`left` заставляет браузер заново посчитать позиции соседних элементов (reflow). `transform` (и `opacity`) обрабатываются на отдельном composite-слое GPU — соседние элементы не пересчитываются.

**Вывод:** для анимаций перемещения/масштабирования используй `transform`, а не `top`/`left`/`width`/`height`.
