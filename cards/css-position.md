---
id: css-position
category: Frontend
daily: true
---
# Какие значения есть у CSS-свойства `position`?
## Ответ
| Значение | Поведение |
|---|---|
| `static` | По умолчанию, в нормальном потоке |
| `relative` | В потоке, смещается от своего исходного места |
| `absolute` | Вырван из потока, позиционируется от ближайшего non-static предка |
| `fixed` | Вырван из потока, позиционируется от viewport |
| `sticky` | В потоке до порогового значения, затем фиксируется |

```css
.parent { position: relative; }
.child  { position: absolute; top: 0; right: 0; }

.header { position: sticky; top: 0; }
```

`z-index` работает только у элементов с `position` ≠ `static`.
