---
id: react-portals
category: Frontend
daily: true
---

# Что такое React Portals и зачем они нужны?

## Ответ

`createPortal` рендерит дочерние элементы в **другой DOM-узел**, вне обычной иерархии родителя, но сохраняя их в исходном месте **React-дерева** (события всплывают как обычно, контекст работает).

```jsx
import { createPortal } from "react-dom";

function Modal({ children }) {
  return createPortal(
    <div className="modal-overlay">{children}</div>,
    document.getElementById("modal-root")
  );
}
```

```html
<body>
  <div id="root"></div>
  <div id="modal-root"></div>
</body>
```

Зачем нужен: модальные окна, тултипы, всплывающие уведомления — им нужно визуально находиться поверх всего (`z-index`), а `overflow: hidden` или `position` родителя не должны их обрезать.

Важно: portal — это только про **место в DOM**, не про React-дерево. Обработчик `onClick` на дочернем элементе всё равно всплывёт к родительскому компоненту, а не к `#modal-root`.
