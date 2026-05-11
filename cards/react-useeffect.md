---
id: react-useeffect
category: Frontend
daily: true
---

# Когда запускается useEffect и что такое массив зависимостей?

## Ответ

`useEffect` запускается **после рендера**. Массив зависимостей определяет, когда именно.

```jsx
useEffect(() => {
  // Запускается после каждого рендера
});

useEffect(() => {
  // Запускается один раз — при монтировании
}, []);

useEffect(() => {
  // Запускается при изменении userId
  fetchUser(userId);
}, [userId]);

useEffect(() => {
  const timer = setInterval(tick, 1000);
  return () => clearInterval(timer); // cleanup при размонтировании
}, []);
```

Забытая зависимость → устаревшие данные (stale closure). Лишняя зависимость → лишние вызовы.
