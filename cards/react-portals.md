---
id: react-portals
category: Frontend
difficulty: junior
daily: true
---

# Что такое React Portals и зачем они нужны?

## Ответ

**Portal** позволяет отрендерить дочерний компонент в другой DOM-узел, вне иерархии родителя — но React всё равно относится к нему как к обычному дочернему элементу (события всплывают, контекст работает).

```jsx
import { createPortal } from 'react-dom';

function Modal({ children }) {
  return createPortal(
    <div className="modal-overlay">{children}</div>,
    document.getElementById('modal-root') // отдельный узел вне #root
  );
}
```

```html
<body>
  <div id="root"></div>
  <div id="modal-root"></div>
</body>
```

**Зачем нужен:** модалки, тултипы и дропдауны часто «обрезаются» родителем с `overflow: hidden` или перекрываются из-за `z-index` внутри сложной иерархии. Portal рендерит их в корень `<body>`, минуя эти ограничения, сохраняя логическую связь с React-деревом (события `onClick` всплывают до родительского React-компонента, а не до DOM-родителя).
