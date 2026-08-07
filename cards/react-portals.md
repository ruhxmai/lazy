---
id: react-portals
category: Frontend
difficulty: junior
daily: true
---

# Что такое React Portal и зачем он нужен?

## Ответ

`createPortal` рендерит дочерние элементы в **другой DOM-узел**, вне обычной иерархии родителя — но React-дерево (контекст, события) остаётся прежним.

```jsx
import { createPortal } from 'react-dom';

function Modal({ children }) {
  return createPortal(
    <div className="modal">{children}</div>,
    document.getElementById('modal-root')
  );
}
```

**Зачем это нужно:** модалки, тултипы, всплывающие меню часто «ломаются» из-за `overflow: hidden` или `z-index` родителя. Портал выводит их прямо в `<body>`, минуя эти ограничения, но `onClick` всё равно всплывает через React-дерево, а не через DOM-дерево.

- В `index.html` заранее нужен контейнер: `<div id="modal-root"></div>`
- Событие, всплывающее из портала, ловится обработчиками React-родителя, а не DOM-родителя
