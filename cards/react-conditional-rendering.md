---
id: react-conditional-rendering
category: Frontend
difficulty: junior
daily: true
---

# Какие способы условного рендеринга есть в React?

## Ответ

Самые частые способы показать разный JSX в зависимости от условия:

**1. Тернарный оператор** — когда есть два варианта:
```jsx
{isLoggedIn ? <Dashboard /> : <LoginForm />}
```

**2. Логическое `&&`** — когда нужно показать элемент или ничего:
```jsx
{items.length > 0 && <ItemList items={items} />}
```

**3. Ранний return** — когда условий несколько:
```jsx
function Profile({ user }) {
  if (!user) return <Spinner />;
  if (user.banned) return <BannedMessage />;
  return <UserCard user={user} />;
}
```

**Частая ошибка:** `{count && <Badge count={count} />}` — если `count` равен `0`, React отрендерит **само число `0`** на экране, а не пустоту, потому что `0` — falsy, но не `null`/`undefined`/`false`. Решение: `{count > 0 && <Badge count={count} />}`.
