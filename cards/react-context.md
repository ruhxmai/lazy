---
id: react-context
category: Frontend
difficulty: junior
daily: true
---

# Что такое React Context и зачем он нужен?

## Ответ

Context позволяет передавать данные через дерево компонентов без props drilling — без передачи пропсов через каждый уровень.

```js
// 1. Создаём контекст
const ThemeContext = React.createContext('light');

// 2. Оборачиваем провайдером
function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Header />
    </ThemeContext.Provider>
  );
}

// 3. Читаем в любом потомке
function Header() {
  const theme = useContext(ThemeContext);
  return <div className={theme}>Header</div>;
}
```

- `createContext(defaultValue)` — создаёт контекст
- `Provider` — передаёт значение всем потомкам
- `useContext(Context)` — читает значение в компоненте
- Используй для: темы, язык интерфейса, текущий пользователь
