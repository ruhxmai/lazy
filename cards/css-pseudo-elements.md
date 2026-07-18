---
id: css-pseudo-elements
category: Frontend
difficulty: junior
daily: true
---

# Чем псевдоэлементы (`::before`, `::after`) отличаются от псевдоклассов?

## Ответ

**Псевдокласс** (`:hover`, `:focus`, `:nth-child`) описывает **состояние** существующего элемента.

**Псевдоэлемент** (`::before`, `::after`, `::first-line`) создаёт **виртуальный подэлемент** внутри выбранного, которого нет в HTML-разметке. Обязательно требует свойство `content`, иначе не отобразится.

```css
.button::before {
  content: "→ ";
  color: gray;
}

.tooltip:hover::after {
  content: attr(data-tip);
  position: absolute;
  background: #333;
  color: #fff;
}
```

**Правило записи:** псевдокласс — одно двоеточие (`:hover`), псевдоэлемент — два (`::before`). Старый CSS2-синтаксис (`:before` с одним двоеточием) до сих пор поддерживается браузерами для совместимости, но в новом коде используют `::before`.

Частые применения `::before`/`::after`: декоративные иконки, кавычки, очистка float (`clearfix`), нумерация без изменения HTML.
