---
id: css-position
category: Frontend
daily: true
---
# Чем отличаются значения свойства CSS position?

## Ответ

| Значение   | Поток документа | Позиционируется относительно |
|------------|----------------|------------------------------|
| `static`   | Да (умолчание) | — |
| `relative` | Да             | Своего нормального места |
| `absolute` | Нет            | Ближайшего не-static родителя |
| `fixed`    | Нет            | Viewport (не скроллируется) |
| `sticky`   | Да             | Родителя (прилипает при скролле) |

```css
.parent { position: relative; }
.badge  { position: absolute; top: 0; right: 0; }
.header { position: sticky; top: 0; }
```
