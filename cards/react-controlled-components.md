---
id: react-controlled-components
category: Frontend
difficulty: junior
daily: true
---

# Чем управляемый (controlled) input отличается от неуправляемого (uncontrolled)?

## Ответ

**Controlled** — значение поля хранится в состоянии React (`useState`), а не в DOM. React полностью управляет вводом.

```jsx
function ControlledInput() {
  const [value, setValue] = useState('');

  return (
    <input
      value={value}
      onChange={(e) => setValue(e.target.value)}
    />
  );
}
```

**Uncontrolled** — значение хранится в самом DOM-элементе, React обращается к нему только по запросу через `ref`.

```jsx
function UncontrolledInput() {
  const inputRef = useRef(null);

  const handleSubmit = () => {
    console.log(inputRef.current.value);
  };

  return <input ref={inputRef} defaultValue="" />;
}
```

| | Controlled | Uncontrolled |
|---|---|---|
| Источник правды | React state | DOM |
| Валидация на лету | Легко | Сложнее |
| Ре-рендер на каждый символ | Да | Нет |
| Простые формы | Избыточно | Проще |

**Частая ошибка:** передать `value` без `onChange` — React выдаст warning про read-only поле, а пользователь не сможет ничего ввести.
