---
id: css-positioning
category: Frontend
daily: true
---

# Чем отличаются position: static, relative, absolute, fixed и sticky?

## Ответ

| Значение | В потоке | Отсчёт координат от |
|----------|----------|----------------------|
| `static` | Да | — (по умолчанию) |
| `relative` | Да | Своей исходной позиции |
| `absolute` | Нет | Ближайшего positioned предка |
| `fixed` | Нет | Viewport |
| `sticky` | Да* | Viewport (после threshold) |

```css
/* absolute ищет ближайшего предка с position != static */
.parent { position: relative; }
.child  { position: absolute; top: 0; right: 0; }

/* fixed — всегда у края экрана */
.modal { position: fixed; top: 50%; left: 50%; transform: translate(-50%, -50%); }

/* sticky — прилипает при скролле */
.header { position: sticky; top: 0; z-index: 10; }
```

`absolute` и `fixed` выбивают элемент из потока — родитель "теряет" их высоту.
