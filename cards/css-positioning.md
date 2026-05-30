---
id: css-positioning
category: Frontend
daily: true
---

# Чем отличаются `position: relative`, `absolute`, `fixed` и `sticky`?

## Ответ

| Значение | В потоке | Позиционирование |
|----------|----------|------------------|
| `static` | да | по умолчанию, top/left не работают |
| `relative` | да | смещается от своего обычного места |
| `absolute` | нет | относительно ближайшего предка с position |
| `fixed` | нет | относительно viewport, не скроллится |
| `sticky` | да | relative + фиксируется при прокрутке |

```css
.dropdown {
  position: relative; /* задаём контекст */
}
.dropdown-menu {
  position: absolute; /* прилипает к .dropdown */
  top: 100%;
  left: 0;
}
```
