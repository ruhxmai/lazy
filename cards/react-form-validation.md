---
id: react-form-validation
category: Frontend
difficulty: junior
daily: true
---

# Как валидировать формы в React?

## Ответ

Базовый подход — хранить значения и ошибки в состоянии, валидировать при изменении или отправке.

```jsx
function LoginForm() {
  const [email, setEmail] = useState('');
  const [error, setError] = useState('');

  function validate(value) {
    if (!value.includes('@')) return 'Введите корректный email';
    return '';
  }

  function handleChange(e) {
    const value = e.target.value;
    setEmail(value);
    setError(validate(value));
  }

  function handleSubmit(e) {
    e.preventDefault();
    const validationError = validate(email);
    if (validationError) {
      setError(validationError);
      return;
    }
    // отправка формы
  }

  return (
    <form onSubmit={handleSubmit}>
      <input value={email} onChange={handleChange} />
      {error && <p className="error">{error}</p>}
      <button type="submit">Войти</button>
    </form>
  );
}
```

**Ключевые моменты:**
- Валидировать можно "на лету" (при каждом изменении) или только при `submit` — выбор зависит от UX
- `e.preventDefault()` обязателен, иначе браузер перезагрузит страницу
- Для сложных форм с множеством полей используют библиотеки (`react-hook-form`, `Formik`), чтобы не писать состояние вручную для каждого поля

```jsx
// react-hook-form сокращает бойлерплейт
const { register, handleSubmit, formState: { errors } } = useForm();
```
