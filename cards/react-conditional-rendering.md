---
id: react-conditional-rendering
category: Frontend
daily: true
---
# Как правильно делать условный рендеринг в React и какая тут частая ошибка?

## Ответ

Три основных способа:

```jsx
// 1. Тернарный оператор — когда есть обе ветки
{isLoggedIn ? <Dashboard /> : <LoginForm />}

// 2. && — когда нужна только одна ветка
{hasError && <ErrorBanner message={error} />}

// 3. Ранний return — когда веток много или логика сложная
function Page({ user }) {
  if (!user) return <Spinner />;
  if (user.banned) return <BannedNotice />;
  return <Dashboard user={user} />;
}
```

**Частая ловушка с `&&`:** если левая часть — число `0`, React отрендерит **сам `0`** на странице, а не «ничего», потому что `0` — валидный рендерящийся узел (в отличие от `false`, `null`, `undefined`).

```jsx
// ❌ Если items.length === 0, на экране появится "0"
{items.length && <List items={items} />}

// ✅ Приводим к boolean явно
{items.length > 0 && <List items={items} />}
{Boolean(items.length) && <List items={items} />}
```
