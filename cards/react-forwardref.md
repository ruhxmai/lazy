---
id: react-forwardref
category: Frontend
difficulty: junior
daily: true
---

# Зачем нужен `forwardRef` в React?

## Ответ

По умолчанию `ref` — не обычный проп: React обрабатывает его особо и **не передаёт** внутрь функционального компонента. Если родителю нужен доступ к DOM-узлу внутри дочернего компонента, `ref` нужно явно «переслать» через `forwardRef`.

```jsx
const Input = forwardRef((props, ref) => (
  <input ref={ref} className="styled-input" {...props} />
));

function Form() {
  const inputRef = useRef(null);

  const focusInput = () => inputRef.current.focus();

  return (
    <>
      <Input ref={inputRef} placeholder="Имя" />
      <button onClick={focusInput}>Фокус на поле</button>
    </>
  );
}
```

Без `forwardRef` попытка передать `ref` обычному функциональному компоненту (`<Input ref={inputRef} />`) даст `undefined` в `inputRef.current` (или предупреждение в консоли) — компонент не знает, что делать с `ref`.

**Типичные случаи использования:** библиотеки UI-компонентов (кастомный `Input`, `Button`), где нужно дать доступ к нативному DOM-элементу изнутри обёртки, не ломая инкапсуляцию остальных пропсов.
