---
id: react-memo
category: Frontend
daily: true
---
# Чем `React.memo` отличается от `useMemo`?

## Ответ

**`React.memo`** — оборачивает **компонент**. Пропускает повторный рендер компонента, если пропсы не изменились (сравнение поверхностное, по ссылкам).

```js
const UserCard = React.memo(function UserCard({ user }) {
  console.log('render UserCard');
  return <div>{user.name}</div>;
});

// Родитель ре-рендерится, но UserCard — нет, если user та же ссылка
```

**`useMemo`** — мемоизирует **значение** внутри компонента (результат вычисления), а не сам компонент.

```js
const sortedList = useMemo(() => {
  return items.slice().sort((a, b) => a.price - b.price);
}, [items]);
```

**Частая ловушка:** `React.memo` не поможет, если родитель каждый раз создаёт новый объект/функцию в пропсах — ссылка меняется, и сравнение считает пропсы разными:

```js
// UserCard всё равно ре-рендерится — onClick новая функция каждый раз
<UserCard user={user} onClick={() => doSomething()} />

// Решение — стабилизировать функцию через useCallback
const handleClick = useCallback(() => doSomething(), []);
<UserCard user={user} onClick={handleClick} />
```

`React.memo` защищает **компонент** от лишнего рендера, `useMemo`/`useCallback` — стабилизируют **данные и функции**, которые в этот компонент передаются.
