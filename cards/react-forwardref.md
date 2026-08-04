---
id: react-forwardref
category: Frontend
difficulty: junior
daily: true
---

# Зачем нужен forwardRef в React?

## Ответ

По умолчанию `ref` нельзя передать в кастомный компонент — React резервирует проп `ref` для получения DOM-узла и не прокидывает его дальше автоматически.

```jsx
function Input(props) {
  return <input {...props} />;
}

// myRef.current будет undefined — ref не долетит до <input>
<Input ref={myRef} />;
```

`forwardRef` оборачивает компонент и явно «прокидывает» `ref` вторым аргументом:

```jsx
const Input = forwardRef((props, ref) => {
  return <input ref={ref} {...props} />;
});

<Input ref={myRef} />; // myRef.current === DOM-элемент <input>
```

Чаще всего нужен для переиспользуемых UI-компонентов (кнопки, инпуты, модалки), когда родителю нужен прямой доступ к DOM-узлу — например, чтобы вызвать `.focus()`.
