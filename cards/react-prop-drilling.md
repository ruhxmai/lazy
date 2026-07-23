---
id: react-prop-drilling
category: Frontend
difficulty: junior
daily: true
---

# Что такое prop drilling и как с ним бороться?

## Ответ

**Prop drilling** — ситуация, когда проп нужно передать через несколько промежуточных компонентов, которым он сам не нужен, просто чтобы он дошёл до глубоко вложенного потомка.

```jsx
function App() {
  const user = { name: "Anna" };
  return <Layout user={user} />;
}
function Layout({ user }) {
  return <Sidebar user={user} />; // Layout проп не использует, просто передаёт дальше
}
function Sidebar({ user }) {
  return <UserBadge user={user} />; // тоже просто транзит
}
function UserBadge({ user }) {
  return <span>{user.name}</span>; // а вот тут проп реально нужен
}
```

Проблема растёт вместе с деревом компонентов: любое изменение формы данных требует правки всех промежуточных компонентов.

**Способы решения:**

- **Context API** — данные кладутся в контекст один раз наверху и читаются напрямую там, где нужны:

```jsx
const UserContext = createContext(null);

function App() {
  return (
    <UserContext.Provider value={{ name: "Anna" }}>
      <Layout />
    </UserContext.Provider>
  );
}
function UserBadge() {
  const user = useContext(UserContext);
  return <span>{user.name}</span>;
}
```

- **Composition (children/slots)** — передавать готовый JSX через `children`, а не проп с данными.
- **Менеджер состояния** (Redux, Zustand, Recoil) — для сложных приложений с множеством разрозненных потребителей одних и тех же данных.
