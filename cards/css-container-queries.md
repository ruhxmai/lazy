---
id: css-container-queries
category: Frontend
difficulty: junior
daily: true
---

# Чем container queries отличаются от media queries?

## Ответ

**Media query** реагирует на размер **окна браузера (viewport)**:

```css
@media (min-width: 768px) {
  .card { flex-direction: row; }
}
```

Проблема: компонент не знает, в какой части страницы он находится — стили ломаются, если один и тот же компонент используется и в узком сайдбаре, и в широкой колонке.

**Container query** реагирует на размер **родительского контейнера**, а не всего окна:

```css
.layout {
  container-type: inline-size;
  container-name: card-wrapper;
}

@container card-wrapper (min-width: 400px) {
  .card { flex-direction: row; }
}
```

Теперь `.card` адаптируется к ширине своего контейнера — в узком сайдбаре останется вертикальным, а в широкой колонке станет горизонтальным, независимо от размера окна браузера.

Ключевое правило: элемент с `container-type` **сам не может** реагировать на собственный размер через `@container` — только его дочерние элементы.
