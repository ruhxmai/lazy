---
id: css-position
category: Frontend
difficulty: junior
daily: true
---

# Как работает свойство position в CSS?

## Ответ

| Значение | Поведение |
|----------|-----------|
| `static` | По умолчанию, элемент в нормальном потоке |
| `relative` | Смещается от своего обычного места; место в потоке сохраняется |
| `absolute` | Вырывается из потока; позиционируется относительно ближайшего не-`static` предка |
| `fixed` | Как `absolute`, но относительно viewport; не скроллится |
| `sticky` | Ведёт себя как `relative`, пока не достигнет порога — затем фиксируется |

```css
.parent { position: relative; }
.badge  { position: absolute; top: 0; right: 0; }
```

`absolute` и `fixed` убирают элемент из потока — остальные элементы его «не видят».
