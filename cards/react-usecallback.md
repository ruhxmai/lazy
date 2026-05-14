---
id: react-usecallback
category: Frontend
difficulty: junior
daily: true
---

# Зачем нужен хук useCallback в React?

## Ответ

`useCallback` мемоизирует функцию — возвращает ту же ссылку при повторном рендере, если зависимости не изменились. Предотвращает лишние рендеры дочерних компонентов.

```js
const handleClick = useCallback(() => {
  doSomething(id);
}, [id]); // пересоздаётся только при изменении id
```

Используй когда:
- передаёшь функцию в `React.memo`-компонент
- функция попадает в зависимости `useEffect`

Похожий хук **useMemo** мемоизирует вычисленное значение:

```js
const filtered = useMemo(() => list.filter(x => x.active), [list]);
```
