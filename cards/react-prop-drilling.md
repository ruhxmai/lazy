---
id: react-prop-drilling
category: Frontend
difficulty: junior
daily: true
---

# Что такое prop drilling и как его избежать?

## Ответ

Prop drilling — ситуация, когда данные передаются через несколько промежуточных компонентов, которым эти props не нужны, просто чтобы «докинуть» их до глубоко вложенного потомка.

```jsx
function App() {
  const user = { name: "Anna" };
  return <Layout user={user} />;
}
function Layout({ user }) {
  return <Sidebar user={user} />; // сам не использует user
}
function Sidebar({ user }) {
  return <Profile user={user} />;
}
```

Проблема: если поменять структуру данных, придётся править все промежуточные компоненты.

**Как избежать:**
- **Context API** — передать данные напрямую без промежуточных пропсов
- **Стейт-менеджеры** (Redux, Zustand, Recoil)
- **Композиция компонентов** — передавать `children` вместо конкретных пропсов
