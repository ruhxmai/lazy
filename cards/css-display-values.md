---
id: css-display-values
category: Frontend
daily: true
---

# Чем отличаются display: block, inline и inline-block?

## Ответ

**`block`** — элемент занимает всю доступную ширину, начинается с новой строки, поддерживает `width`, `height`, вертикальные `margin`/`padding` (`<div>`, `<p>`, `<h1>`).

**`inline`** — элемент течёт внутри строки текста, **не** поддерживает `width`/`height` и вертикальные `margin` (`<span>`, `<a>`, `<strong>`).

**`inline-block`** — течёт как `inline` (в строке), но поддерживает `width`, `height` и все `margin`/`padding`, как `block`.

```css
.block { display: block; }        /* новая строка, можно задать width/height */
.inline { display: inline; }      /* в строке, width/height игнорируются */
.inline-block { display: inline-block; } /* в строке, но width/height работают */
```

```html
<span style="width: 100px; height: 50px; background: red;">
  inline — width/height не применятся
</span>

<span style="display: inline-block; width: 100px; height: 50px; background: green;">
  inline-block — width/height применятся
</span>
```

| Свойство | block | inline | inline-block |
|---|---|---|---|
| Новая строка | Да | Нет | Нет |
| `width` / `height` | Да | Игнорируется | Да |
| Вертикальный `margin`/`padding` | Да | Игнорируется (визуально) | Да |
| Пример тега | `div`, `p` | `span`, `a` | `img`, `button` |

> Частая ошибка junior-разработчика: пытаться задать `width` элементу с `display: inline` и не понимать, почему это не работает.
