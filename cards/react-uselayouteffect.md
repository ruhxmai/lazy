---
id: react-uselayouteffect
category: Frontend
difficulty: junior
daily: true
---

# useEffect vs useLayoutEffect — в чём разница?

## Ответ

Оба хука запускают побочный эффект после рендера компонента, но в разный момент времени:

- **useEffect** — асинхронно, **после** того как браузер отрисовал кадр на экране
- **useLayoutEffect** — синхронно, **до** отрисовки — браузер ждёт, пока эффект не выполнится

```js
useEffect(() => {
  console.log('после того как браузер показал кадр пользователю');
});

useLayoutEffect(() => {
  console.log('до показа кадра, блокирует отрисовку');
});
```

**Когда нужен useLayoutEffect:** если эффект синхронно меняет DOM и это изменение должно быть видно сразу, без «мигания» — например, измерить размер/позицию элемента через `getBoundingClientRect()` и тут же поправить стиль, пока пользователь ничего не увидел.

```js
function Tooltip() {
  const ref = useRef(null);

  useLayoutEffect(() => {
    const { height } = ref.current.getBoundingClientRect();
    if (height > 200) {
      ref.current.style.top = '0px'; // применится ДО отрисовки — без мигания
    }
  }, []);

  return <div ref={ref}>...</div>;
}
```

**Правило:** по умолчанию используйте `useEffect` — он не блокирует отрисовку и не тормозит UI. `useLayoutEffect` — только когда без него виден визуальный «прыжок» на экране.