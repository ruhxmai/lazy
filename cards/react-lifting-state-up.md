---
id: react-lifting-state-up
category: Frontend
difficulty: junior
daily: true
---

# Что такое prop drilling и как его решает lifting state up?

## Ответ

**Prop drilling** — ситуация, когда проп передаётся через несколько промежуточных компонентов, которым он сам не нужен, только чтобы попасть к глубоко вложенному потомку.

**Lifting state up** («поднятие состояния») — паттерн, при котором состояние переносится в ближайшего общего родителя двух компонентов, которым нужно его использовать или синхронизировать.

```jsx
// До: у компонентов несвязанное состояние
function Search() {
  const [query, setQuery] = useState('');
  return <input value={query} onChange={e => setQuery(e.target.value)} />;
}
function Results() {
  // нет доступа к query
}

// После: состояние поднято в общего родителя
function App() {
  const [query, setQuery] = useState('');
  return (
    <>
      <Search query={query} onChange={setQuery} />
      <Results query={query} />
    </>
  );
}
```

- Если проп приходится «прокидывать» через 3+ уровня — сигнал задуматься о `Context` вместо lifting state up
- Lifting state up не заменяет Context/Redux, а решает более простые локальные случаи
