---
id: react-custom-hooks
category: Frontend
daily: true
---
# Что такое custom hook в React и зачем он нужен?
## Ответ
Custom hook — функция, начинающаяся с `use`, которая переиспользует логику с состоянием и эффектами между компонентами.

```js
// Создание custom hook
function useWindowWidth() {
  const [width, setWidth] = useState(window.innerWidth);
  useEffect(() => {
    const handler = () => setWidth(window.innerWidth);
    window.addEventListener('resize', handler);
    return () => window.removeEventListener('resize', handler);
  }, []);
  return width;
}

// Использование в любом компоненте
function MyComponent() {
  const width = useWindowWidth();
  return <p>Width: {width}px</p>;
}
```

Главное: имя должно начинаться с `use`, иначе React не применяет правила хуков. Заменяет HOC и render props без лишней вложенности.
