---
id: css-position
category: Frontend
difficulty: junior
daily: true
---

# Чем отличаются значения свойства CSS position?

## Ответ

`position` управляет тем, как элемент позиционируется в документе.

```css
/* static — по умолчанию, top/left/right/bottom не работают */
.box { position: static; }

/* relative — смещается относительно своего обычного места */
.box { position: relative; top: 10px; left: 20px; }

/* absolute — вырывается из потока, привязывается к ближайшему
   родителю с position != static */
.child { position: absolute; top: 0; right: 0; }

/* fixed — фиксируется относительно viewport (окна браузера),
   не скроллится вместе со страницей */
.header { position: fixed; top: 0; width: 100%; }

/* sticky — как relative, но "прилипает" при прокрутке */
.nav { position: sticky; top: 0; }
```

- `absolute` и `fixed` удаляют элемент из нормального потока
- `sticky` требует хотя бы одно из: `top`, `bottom`, `left`, `right`
- Для `absolute` нужен родитель с `position: relative` (или другим non-static)
