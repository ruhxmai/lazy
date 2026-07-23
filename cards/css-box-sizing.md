---
id: css-box-sizing
category: Frontend
difficulty: junior
daily: true
---

# Что такое `box-sizing: border-box`?

## Ответ

**`box-sizing`** определяет, что именно входит в заданную `width`/`height` элемента.

```css
.content-box {
  box-sizing: content-box; /* по умолчанию */
  width: 200px;
  padding: 20px;
  border: 5px solid;
  /* итоговая ширина на экране = 200 + 20*2 + 5*2 = 250px */
}

.border-box {
  box-sizing: border-box;
  width: 200px;
  padding: 20px;
  border: 5px solid;
  /* итоговая ширина на экране = 200px, padding и border "съедают" место внутри */
}
```

Почти все современные проекты ставят глобально:

```css
*, *::before, *::after {
  box-sizing: border-box;
}
```

Это делает вёрстку предсказуемой — заданная ширина остаётся шириной, независимо от паддингов и рамок.
