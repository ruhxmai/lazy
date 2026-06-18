---
id: react-custom-hooks
category: Frontend
daily: true
---
# Что такое кастомный хук в React и когда его создавать?
## Ответ
Кастомный хук — обычная JS-функция, имя которой начинается с `use`, внутри которой вызываются стандартные хуки React. Служит для извлечения и переиспользования логики между компонентами.

```js
// Хук для синхронизации состояния с localStorage
function useLocalStorage(key, initialValue) {
  const [value, setValue] = useState(
    () => JSON.parse(localStorage.getItem(key)) ?? initialValue
  );

  const setStored = (newValue) => {
    setValue(newValue);
    localStorage.setItem(key, JSON.stringify(newValue));
  };

  return [value, setStored];
}

// Использование в компоненте
const [theme, setTheme] = useLocalStorage('theme', 'light');
```

Создавай кастомный хук, когда логика с хуками дублируется в 2+ компонентах.
