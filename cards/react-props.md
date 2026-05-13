---
id: react-props
category: Frontend
difficulty: junior
daily: true
---

# Что такое props в React и как их передавать?

## Ответ

`props` (свойства) — данные, которые родительский компонент передаёт дочернему. Props доступны только для чтения.

```jsx
// Родитель
function App() {
  return <Button label="Сохранить" onClick={() => alert('Сохранено!')} />;
}

// Дочерний компонент
function Button({ label, onClick }) {
  return <button onClick={onClick}>{label}</button>;
}
```

- Props передаются как атрибуты JSX
- Внутри компонента менять props нельзя — только через состояние родителя
- Деструктуризация `{ label, onClick }` — удобный способ достать нужные props
