---
id: css-position
category: Frontend
daily: true
---

# Чем отличаются position: relative, absolute, fixed и sticky?

## Ответ

| Значение | В потоке | Отсчёт координат от |
|----------|----------|---------------------|
| `static` | да | — (по умолчанию) |
| `relative` | да | самого себя |
| `absolute` | нет | ближайшего non-static предка |
| `fixed` | нет | окна браузера |
| `sticky` | да | контейнера при прокрутке |

```css
.parent { position: relative; }

.child {
  position: absolute;
  top: 0;
  right: 0; /* угол .parent */
}
```

`absolute` ищет ближайшего предка с `position != static`. Если такого нет — позиционируется относительно `<html>`.
