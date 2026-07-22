---
id: css-pseudo-elements
category: Frontend
difficulty: junior
daily: true
---

# Чем псевдоэлементы (`::before`, `::after`) отличаются от псевдоклассов?

## Ответ

**Псевдокласс** (`:hover`, `:first-child`) описывает **состояние** уже существующего элемента. **Псевдоэлемент** (`::before`, `::after`) создаёт **виртуальный элемент** внутри существующего, которого нет в самом HTML.

```css
.tooltip::before {
  content: "→ ";
  color: gray;
}

.required::after {
  content: "*";
  color: red;
}
```

Обязательное условие для `::before`/`::after` — свойство `content`, даже пустое (`content: ""`), иначе элемент не отобразится. Часто применяются для иконок, декоративных элементов и старого приёма `clearfix`.
