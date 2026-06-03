---
id: react-context
category: Frontend
difficulty: junior
daily: true
---

# Что такое React Context и когда его использовать?

## Ответ

Context — механизм React для передачи данных вниз по дереву компонентов **без явного пробрасывания через props** (prop drilling).

**Используй когда:**
- Тема интерфейса (тёмная / светлая)
- Данные авторизованного пользователя
- Язык / локализация

```jsx
const ThemeContext = React.createContext("light");

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Toolbar />
    </ThemeContext.Provider>
  );
}

function Toolbar() {
  const theme = useContext(ThemeContext);
  return <div className={theme}>Hello</div>;
}
```

> Не злоупотребляй Context для часто меняющихся данных — каждое изменение вызывает ре-рендер **всех** потребителей.
