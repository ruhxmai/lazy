---
id: css-inheritance
category: Frontend
difficulty: junior
daily: true
---

# Какие CSS-свойства наследуются от родителя, а какие нет?

## Ответ

Наследуются в основном свойства **текста**: `color`, `font-family`, `font-size`, `line-height`, `text-align`, `visibility`.

Не наследуются свойства **блочной модели**: `margin`, `padding`, `border`, `width`, `height`, `background`, `display`.

```css
.parent {
  color: blue;       /* унаследуется детьми */
  border: 1px solid; /* НЕ унаследуется */
}
```

Управлять наследованием вручную можно ключевыми словами:

- `inherit` — взять значение у родителя
- `initial` — сбросить к значению по умолчанию
- `unset` — `inherit`, если свойство наследуемое, иначе `initial`
