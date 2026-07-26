---
id: react-portals
category: React
difficulty: junior
daily: true
---

# Что такое React Portal и зачем он нужен?

## Ответ

`createPortal` позволяет отрендерить дочерние элементы **в другой DOM-узел**, вне иерархии родительского компонента, при этом сохраняя место компонента в React-дереве (контекст, события `bubbling` работают как обычно).

```jsx
import { createPortal } from "react-dom";

function Modal({ children }) {
  return createPortal(
    <div className="modal">{children}</div>,
    document.getElementById("modal-root")
  );
}
```

Зачем нужен:

- Модальные окна, тултипы, всплывающие уведомления — чтобы избежать проблем с `overflow: hidden` и `z-index` родителей.
- DOM-элемент рендерится в `#modal-root`, но события всплывают через React-дерево, как будто портал остался на месте.

```html
<div id="root"></div>
<div id="modal-root"></div>
```
