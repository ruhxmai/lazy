---
id: css-positioning
category: Frontend
daily: true
---
# Чем отличаются значения свойства position в CSS?

## Ответ

| Значение | Поведение |
|----------|-----------|
| `static` | По умолчанию. `top`/`left` не работают |
| `relative` | Смещается от своего обычного места в потоке |
| `absolute` | Позиционируется относительно ближайшего non-static родителя |
| `fixed` | Относительно viewport, не скроллится вместе со страницей |
| `sticky` | Как `relative`, пока не достигнет порога скролла — тогда как `fixed` |

```css
.parent { position: relative; } /* якорь для absolute-детей */

.badge {
  position: absolute;
  top: 8px;
  right: 8px; /* 8px от правого края .parent */
}

.navbar {
  position: sticky;
  top: 0; /* прилипает к верху при скролле */
}
```
