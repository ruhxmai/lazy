---
id: react-props
category: Frontend
difficulty: junior
daily: true
---

# Что такое props в React?

## Ответ

Props (properties) — данные, которые **родительский компонент передаёт дочернему**. Внутри дочернего компонента props **неизменяемы**.

```jsx
function Greeting({ name, age }) {
  return <p>{name}, {age} лет</p>;
}

// Использование:
<Greeting name="Алексей" age={25} />
```

Если нужно изменить данные — храни состояние в родителе через `useState` и передавай колбэк-функцию через props.
