---
id: react-usecontext
category: Frontend
daily: true
---

# Для чего нужен хук useContext?

## Ответ

`useContext` даёт доступ к значению контекста без передачи props через цепочку компонентов («prop drilling»).

```jsx
const ThemeContext = React.createContext('light');

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Button />
    </ThemeContext.Provider>
  );
}

function Button() {
  const theme = useContext(ThemeContext);
  return <button className={theme}>Click</button>;
}
```

При изменении значения провайдера все компоненты-потребители автоматически перерендериваются.
