---
id: css-box-sizing
category: Frontend
difficulty: junior
daily: true
---

# Что делает box-sizing: border-box?

## Ответ

По умолчанию (`content-box`) `width`/`height` задают размер только **содержимого** — padding и border добавляются сверху, из-за чего итоговый элемент оказывается больше указанного.

```css
.box {
  box-sizing: content-box; /* значение по умолчанию */
  width: 200px;
  padding: 20px;
  border: 5px solid;
  /* реальная ширина = 200 + 20*2 + 5*2 = 250px */
}
```

`border-box` включает padding и border **внутрь** заданной ширины — элемент не «расползается»:

```css
.box {
  box-sizing: border-box;
  width: 200px;
  padding: 20px;
  border: 5px solid;
  /* реальная ширина остаётся 200px, содержимое сжимается под padding/border */
}
```

Поэтому почти все CSS-резеты начинаются с:

```css
*, *::before, *::after {
  box-sizing: border-box;
}
```
