---
id: react-prop-drilling
category: Frontend
daily: true
---

# Что такое prop drilling и как его избежать?

## Ответ

**Prop drilling** — передача пропсов через несколько промежуточных компонентов, которым эти данные не нужны, лишь чтобы «докинуть» их до глубокого потомка.

```jsx
function App() {
  const user = { name: "Alex" };
  return <Layout user={user} />;
}
function Layout({ user }) {
  // Layout сам не использует user, просто передаёт дальше
  return <Sidebar user={user} />;
}
function Sidebar({ user }) {
  return <UserBadge user={user} />;
}
```

**Как избежать:**

1. **Context API** — расшарить значение без передачи через каждый уровень:

```jsx
const UserContext = createContext();

function App() {
  return (
    <UserContext.Provider value={{ name: "Alex" }}>
      <Layout />
    </UserContext.Provider>
  );
}

function UserBadge() {
  const user = useContext(UserContext);
  return <span>{user.name}</span>;
}
```

2. **Композиция через `children`** — вместо передачи пропсов вниз, собирать дерево компонентов снаружи.
3. **Стейт-менеджеры** (Redux, Zustand, Jotai) — для больших приложений с множеством несвязанных потребителей одного состояния.

> Context — не замена стейт-менеджеру: он не оптимизирован для частых обновлений (все потребители перерендерятся).
