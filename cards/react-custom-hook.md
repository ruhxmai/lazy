---
id: react-custom-hook
category: Frontend
daily: true
---

# Что такое Custom Hook в React и зачем он нужен?

## Ответ

**Custom Hook** — функция с именем, начинающимся на `use`, которая содержит логику с хуками React. Позволяет переиспользовать логику между компонентами.

```js
// Кастомный хук для работы с localStorage
function useLocalStorage(key, initialValue) {
  const [value, setValue] = useState(() => {
    const stored = localStorage.getItem(key);
    return stored ? JSON.parse(stored) : initialValue;
  });

  const setStored = (newValue) => {
    setValue(newValue);
    localStorage.setItem(key, JSON.stringify(newValue));
  };

  return [value, setStored];
}

// Использование
function App() {
  const [theme, setTheme] = useLocalStorage("theme", "light");
  return <button onClick={() => setTheme("dark")}>{theme}</button>;
}
```

Custom Hooks убирают дублирование логики без HOC и render-props.
