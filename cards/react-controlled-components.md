---
id: react-controlled-components
category: Frontend
difficulty: junior
daily: true
---

# Чем отличается controlled input от uncontrolled в React?

## Ответ

**Controlled** — значение поля хранится в state React, а не в DOM.

```jsx
function Form() {
  const [value, setValue] = useState('');
  return <input value={value} onChange={(e) => setValue(e.target.value)} />;
}
```

**Uncontrolled** — значение хранит сам DOM, доступ через ref.

```jsx
function Form() {
  const inputRef = useRef();
  const handleSubmit = () => console.log(inputRef.current.value);
  return <input ref={inputRef} defaultValue="" />;
}
```

Controlled даёт полный контроль (валидация на лету, форматирование), но требует ре-рендера на каждый символ. Uncontrolled проще для простых форм.
