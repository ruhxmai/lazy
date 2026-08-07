---
id: css-inheritance
category: Frontend
difficulty: junior
daily: true
---

# Какие CSS-свойства наследуются от родителя, а какие нет?

## Ответ

**Наследуются** обычно свойства, связанные с текстом: `color`, `font-family`, `font-size`, `line-height`, `text-align`, `visibility`.

**Не наследуются** свойства блочной модели и позиционирования: `margin`, `padding`, `border`, `width`, `height`, `background`, `position`.

```css
.parent {
  color: red;        /* унаследуется детьми */
  border: 1px solid; /* НЕ унаследуется */
}
```

Любое свойство можно принудительно унаследовать или сбросить:

```css
.child {
  color: inherit;  /* взять значение родителя явно */
  border: initial; /* сбросить к значению по умолчанию */
  all: unset;      /* сбросить вообще всё */
}
```

Логика простая: то, что визуально «течёт» через текст, наследуется; то, что задаёт форму и размер конкретного блока, — нет.
