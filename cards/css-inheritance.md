---
id: css-inheritance
category: Frontend
difficulty: junior
daily: true
---

# Что такое наследование (inheritance) в CSS?

## Ответ

Некоторые CSS-свойства автоматически передаются от родителя к потомкам — это и есть **наследование**. Другие свойства по умолчанию не наследуются.

**Наследуются:** `color`, `font-family`, `font-size`, `line-height`, `visibility`

**Не наследуются:** `margin`, `padding`, `border`, `width`, `height`, `background`

```css
body {
  color: #333;
  font-family: Arial, sans-serif;
}
/* весь текст внутри body унаследует эти свойства */
```

Управлять наследованием явно можно с помощью ключевых слов:

```css
.child {
  color: inherit;  /* принудительно взять значение родителя */
  border: initial; /* сбросить к значению по умолчанию браузера */
  all: unset;      /* сбросить вообще всё */
}
```
