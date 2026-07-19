---
id: react-portals
category: Frontend
daily: true
---

# Что такое React Portals и когда их использовать?

## Ответ

**Portal** — способ отрендерить дочерний компонент в DOM-узел, который находится **вне** родительского дерева DOM, но остаётся частью дерева React (контекст, события, порядок вызова хуков — всё как обычно).

```jsx
import { createPortal } from 'react-dom';

function Modal({ children }) {
  return createPortal(
    <div className="modal-overlay">{children}</div>,
    document.getElementById('modal-root') // отдельный узел вне #root
  );
}

function App() {
  return (
    <div className="app" style={{ overflow: 'hidden' }}>
      <Modal>Это окно не обрежется overflow: hidden родителя</Modal>
    </div>
  );
}
```

**Зачем нужны:**

- Модальные окна, тултипы, dropdown-меню — контент должен визуально «вырваться» за пределы контейнера с `overflow: hidden` или `z-index`-конфликтами.
- Рендер в `<body>` напрямую, минуя ограничения родительских стилей.

**Важно:** несмотря на другое место в DOM, **всплытие событий (event bubbling) идёт по React-дереву**, а не по DOM-дереву. Клик внутри портала всплывёт к родительским React-обработчикам так же, как если бы портала не было.
