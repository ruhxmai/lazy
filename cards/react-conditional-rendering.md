---
id: react-conditional-rendering
category: Frontend
daily: true
---

# Какие есть способы условного рендеринга в React и в чём подвох `&&`?

## Ответ

Основные способы:

```jsx
// 1. Тернарный оператор — если нужны обе ветки
{isLoggedIn ? <Dashboard /> : <Login />}

// 2. && — если нужна только одна ветка
{items.length > 0 && <List items={items} />}

// 3. Ранний return — для целых компонентов
function Profile({ user }) {
  if (!user) return null;
  return <div>{user.name}</div>;
}
```

**Подвох `&&`**: если левая часть — это `0`, React отрендерит `0` на экране, а не «ничего».

```jsx
// Баг: если items.length === 0, на странице появится "0"
{items.length && <List items={items} />}

// Исправление: явное приведение к boolean
{items.length > 0 && <List items={items} />}
```

`false`, `null`, `undefined` React не рендерит, а `0` и `""` — рендерит как текст, потому что это валидные React-дети.
