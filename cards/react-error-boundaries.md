---
id: react-error-boundaries
category: Frontend
daily: true
---

# Что такое Error Boundary в React?

## Ответ

**Error Boundary** — компонент, который перехватывает JS-ошибки в дереве дочерних компонентов **во время рендера**, показывает fallback-UI вместо краша всего приложения и логирует ошибку.

Реализуется только через **классовый компонент** с `static getDerivedStateFromError` и/или `componentDidCatch` — хуков для этого нет.

```jsx
class ErrorBoundary extends React.Component {
  state = { hasError: false };

  static getDerivedStateFromError(error) {
    return { hasError: true };
  }

  componentDidCatch(error, info) {
    logErrorToService(error, info);
  }

  render() {
    if (this.state.hasError) {
      return <h2>Что-то пошло не так.</h2>;
    }
    return this.props.children;
  }
}

<ErrorBoundary>
  <UserProfile />
</ErrorBoundary>
```

**Error Boundary НЕ ловит ошибки в:**
- обработчиках событий (`onClick` и т.д.) — там нужен обычный `try/catch`
- асинхронном коде (`setTimeout`, промисы)
- самом Error Boundary
- server-side рендере

> В новых проектах часто используют готовую библиотеку `react-error-boundary` вместо ручной реализации.
