---
id: react-fragment
category: Frontend
daily: true
---

# Зачем нужен React.Fragment и короткий синтаксис <>?

## Ответ

Компонент в React должен возвращать **один корневой элемент**. Если обернуть несколько элементов в `<div>`, в DOM появится лишний узел — это ломает CSS-разметку (например, flex/grid у родителя) и засоряет дерево.

**`React.Fragment`** группирует несколько элементов **без создания реального DOM-узла**.

```jsx
// Плохо: лишний div ломает flex-раскладку родителя
function Row() {
  return (
    <div>
      <td>Имя</td>
      <td>Возраст</td>
    </div>
  );
}

// Хорошо: Fragment не создаёт DOM-узел
function Row() {
  return (
    <React.Fragment>
      <td>Имя</td>
      <td>Возраст</td>
    </React.Fragment>
  );
}

// Короткий синтаксис — то же самое
function Row() {
  return (
    <>
      <td>Имя</td>
      <td>Возраст</td>
    </>
  );
}
```

Короткий синтаксис `<>...</>` **не поддерживает `key`** — если рендерите список фрагментов, нужен явный `React.Fragment key={id}`:

```jsx
items.map(item => (
  <React.Fragment key={item.id}>
    <dt>{item.term}</dt>
    <dd>{item.definition}</dd>
  </React.Fragment>
));
```

> Особенно важно в таблицах: `<tr>` не может содержать `<div>` между собой и `<td>` — только Fragment решает эту проблему без нарушения валидности HTML.
