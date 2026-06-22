---
id: react-memo
category: React
daily: true
---
# Для чего используется React.memo?
## Ответ
`React.memo` — HOC (Higher Order Component), который предотвращает лишние ре-рендеры компонента, если его props не изменились. Сравнивает props поверхностно (shallow comparison).

```jsx
const Button = React.memo(({ onClick, label }) => {
  console.log("render");
  return <button onClick={onClick}>{label}</button>;
});

// Компонент не перерисуется, если onClick и label не изменились
```

Отличие от `useMemo`:
- `React.memo` — оборачивает **компонент**, пропускает его рендер
- `useMemo` — мемоизирует **вычисленное значение** внутри компонента

Для нестабильных коллбэков используйте вместе с `useCallback`, иначе эффект теряется.
