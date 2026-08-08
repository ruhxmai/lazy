---
id: react-prop-drilling
category: Frontend
difficulty: junior
daily: true
---

# Что такое prop drilling и как его избежать?

## Ответ

**Prop drilling** — ситуация, когда пропс приходится прокидывать через много промежуточных компонентов, которым он сам не нужен, просто чтобы передать его дальше вглубь дерева.

```jsx
function App() {
  const user = { name: "Alex" };
  return <Layout user={user} />;
}

function Layout({ user }) {
  return <Sidebar user={user} />; // Layout сам не использует user
}

function Sidebar({ user }) {
  return <Profile user={user} />; // Sidebar тоже не использует
}

function Profile({ user }) {
  return <p>{user.name}</p>; // только здесь user реально нужен
}
```

**Как избежать:**

1. **Context API** — для данных, нужных многим компонентам на разных уровнях
```jsx
const UserContext = createContext();

function App() {
  return (
    <UserContext.Provider value={{ name: "Alex" }}>
      <Layout />
    </UserContext.Provider>
  );
}

function Profile() {
  const user = useContext(UserContext);
  return <p>{user.name}</p>;
}
```

2. **Композиция компонентов** — передавать children вместо пропсов
3. **Менеджеры состояния** (Redux, Zustand) — для сложных приложений с глобальным state
