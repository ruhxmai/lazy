---
id: react-conditional-rendering
category: Frontend
daily: true
---

# Какие способы условного рендеринга есть в React и в чём типичная ошибка с `&&`?

## Ответ

**Тернарный оператор** — когда нужно показать одно из двух:

```jsx
{isLoggedIn ? <Dashboard /> : <LoginForm />}
```

**Логическое `&&`** — когда нужно показать элемент или ничего:

```jsx
{items.length > 0 && <ItemList items={items} />}
```

**Ранний return** — когда условие затрагивает весь компонент:

```jsx
function Profile({ user }) {
  if (!user) return <Spinner />;
  return <div>{user.name}</div>;
}
```

**Частая ошибка с `&&` и числами:**

```jsx
// items.length === 0 → в JSX попадёт число 0, а не "ничего"
{items.length && <ItemList items={items} />}
// Результат на экране: "0"
```

`0`, `NaN` и пустая строка — falsy, но React **рендерит их как текст**, в отличие от `false`, `null`, `undefined` и `true`, которые не рендерятся вообще. Исправление:

```jsx
{items.length > 0 && <ItemList items={items} />}   // ✅ явное сравнение
{Boolean(items.length) && <ItemList items={items} />} // ✅ приведение к boolean
```

Для более чем двух вариантов удобнее объект-словарь вместо цепочки тернарников:

```jsx
const statusView = {
  loading: <Spinner />,
  error: <ErrorMessage />,
  success: <Content />,
};
return statusView[status];
```
