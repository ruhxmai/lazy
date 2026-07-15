---
id: react-lazy-suspense
category: Frontend
difficulty: junior
daily: true
---

# Как сделать code splitting в React с помощью React.lazy и Suspense?

## Ответ

`React.lazy()` позволяет загружать компонент **асинхронно**, отдельным JS-чанком, вместо того чтобы включать его в основной бандл. `Suspense` показывает fallback (например, спиннер), пока чанк грузится.

```jsx
import { lazy, Suspense } from 'react';

const SettingsPage = lazy(() => import('./SettingsPage'));

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <SettingsPage />
    </Suspense>
  );
}
```

Зачем это нужно: пользователь, открывший главную страницу, не должен скачивать код страницы настроек, админки и т.д. — эти чанки подгрузятся, только когда реально понадобятся (например, при переходе по роуту).

- `lazy()` принимает функцию, которая возвращает `import()` — динамический импорт
- `Suspense` может оборачивать несколько lazy-компонентов сразу
- Часто комбинируется с React Router: каждый роут — свой ленивый чанк
- Если во время загрузки произойдёт ошибка — её нужно ловить через Error Boundary, `Suspense` сам ошибки не обрабатывает
