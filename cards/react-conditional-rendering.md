---
id: react-conditional-rendering
category: Frontend
difficulty: junior
daily: true
---

# Какие есть способы условного рендеринга в React?

## Ответ

```jsx
// 1. Тернарный оператор — если/иначе
{isLoggedIn ? <Dashboard /> : <Login />}

// 2. && — рендер только при true
{errors.length > 0 && <ErrorList errors={errors} />}

// 3. Ранний return в компоненте
function Profile({ user }) {
  if (!user) return <Spinner />;
  return <div>{user.name}</div>;
}

// 4. Объект-словарь состояний
const views = { loading: <Spinner />, error: <ErrorMsg />, done: <Data /> };
return views[status];
```

Осторожно с `&&`: если левая часть — число `0`, React отрендерит текст `"0"` на экране вместо пустоты. Лучше писать `count > 0 && ...`, а не `count && ...`.
