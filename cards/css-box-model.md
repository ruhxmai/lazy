---
id: css-box-model
category: Frontend
daily: true
---

# Что такое CSS Box Model и зачем нужен box-sizing: border-box?

## Ответ

Каждый элемент — прямоугольник из 4 слоёв: **content → padding → border → margin**.

```css
/* По умолчанию (content-box): width = только content */
.box {
  width: 200px;
  padding: 20px;
  border: 2px solid black;
  /* реальная ширина = 200 + 40 + 4 = 244px */
}

/* border-box: width включает padding и border */
* { box-sizing: border-box; }
.box {
  width: 200px;
  padding: 20px;
  border: 2px solid black;
  /* реальная ширина = ровно 200px */
}
```

`border-box` удобнее — ширина элемента остаётся предсказуемой. Почти все современные проекты используют `* { box-sizing: border-box; }`.
