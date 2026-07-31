---
id: react-conditional-rendering
category: Frontend
difficulty: junior
daily: true
---

# Какие есть способы условного рендеринга в React?

## Ответ

**Тернарный оператор** — когда нужно показать одно ИЛИ другое:

```jsx
{isLoggedIn ? <Dashboard /> : <Login />}
```

**`&&`** — когда нужно показать элемент ИЛИ ничего:

```jsx
{errors.length > 0 && <ErrorList errors={errors} />}
```

**Ранний `return`** — когда логика ветвления сложная:

```jsx
function Profile({ user }) {
  if (!user) return <Spinner />;
  return <div>{user.name}</div>;
}
```

Осторожно с `&&` и числом `0`: `{count && <Badge />}` отрендерит `0` на экране, если `count === 0`. Правильно — `{count > 0 && <Badge />}`.
