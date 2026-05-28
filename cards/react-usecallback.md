---
id: react-usecallback
category: Frontend
difficulty: junior
daily: true
---

# Зачем нужны useCallback и useMemo в React?

## Ответ

Оба хука **мемоизируют** значения, чтобы не пересчитывать их при каждом рендере.

- `useMemo` — кеширует **результат вычисления** (значение)
- `useCallback` — кеширует **ссылку на функцию**

```js
// Пересчитывается только при изменении items
const doubled = useMemo(() => items.map(x => x * 2), [items]);

// Ссылка на функцию стабильна между рендерами
const handleClick = useCallback(() => {
  doSomething(id);
}, [id]);
```

**Когда применять:**
1. Вычисление тяжёлое (сортировка, фильтрация большого массива)
2. Функция/значение передаётся в дочерний компонент, обёрнутый в `React.memo`

Без `React.memo` на дочернем компоненте смысла в `useCallback` нет.
