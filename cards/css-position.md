---
id: css-position
category: Frontend
daily: true
---

# Чем отличаются position: relative, absolute, fixed и sticky?

## Ответ

| Значение | В потоке | Относительно |
|----------|----------|--------------|
| `static` | Да | — (по умолчанию) |
| `relative` | Да | Самого себя |
| `absolute` | Нет | Ближайшего positioned-предка |
| `fixed` | Нет | Viewport |
| `sticky` | Да | Viewport при прокрутке |

```css
.parent { position: relative; }

/* абсолютно позиционирован внутри .parent */
.child {
  position: absolute;
  top: 10px;
  right: 10px;
}

/* прилипает при прокрутке */
.header {
  position: sticky;
  top: 0;
}
```

`absolute` вырывает элемент из потока; `sticky` остаётся в потоке до момента прилипания.
