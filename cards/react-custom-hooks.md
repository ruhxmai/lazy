---
id: react-custom-hooks
category: Frontend
daily: true
---
# Что такое кастомный хук в React?
## Ответ
Кастомный хук — функция с именем `useXxx`, которая использует встроенные хуки. Позволяет **переиспользовать логику** между компонентами.

```javascript
function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    fetch(url)
      .then(res => res.json())
      .then(data => { setData(data); setLoading(false); });
  }, [url]);

  return { data, loading };
}

// Использование в компоненте:
const { data, loading } = useFetch('/api/users');
```

Правило: кастомный хук не привязан к конкретному компоненту — его можно вызвать в любом месте.
