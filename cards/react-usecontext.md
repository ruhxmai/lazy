---
id: react-usecontext
category: React
daily: true
---
# Когда и как использовать useContext?
## Ответ
`useContext` читает значение из React-контекста без прокидывания props через промежуточные компоненты («prop drilling»).

```jsx
// 1. Создать контекст
const ThemeContext = React.createContext('light');

// 2. Предоставить значение
<ThemeContext.Provider value="dark">
  <App />
</ThemeContext.Provider>

// 3. Читать в любом компоненте дерева
function Button() {
  const theme = useContext(ThemeContext);
  return <button className={theme}>Click</button>;
}
```

Подходит для глобальных данных: тема, язык, текущий пользователь. Для сложной логики лучше Redux / Zustand.
