---
id: css-stacking-context
category: Frontend
daily: true
---

# Что такое stacking context и почему z-index иногда «не работает»?

## Ответ

**Stacking context** — это изолированная группа элементов, внутри которой браузер рассчитывает порядок наложения (z-order) независимо от остального документа.

`z-index` сравнивает элементы **только внутри одного и того же stacking context**. Если элемент попал в дочерний stacking context, никакой `z-index: 9999` не поднимет его выше родителя соседнего контекста.

**Что создаёт новый stacking context:**
- `position: relative/absolute` + указанный `z-index`
- `position: fixed` или `sticky` (всегда)
- `opacity` меньше 1
- `transform`, `filter`, `will-change`, `perspective`
- флекс/грид-контейнер с `z-index` у элемента

```css
.parent-a { position: relative; z-index: 1; }
.child-a  { position: relative; z-index: 9999; } /* заперт внутри .parent-a */

.parent-b { position: relative; z-index: 2; } /* перекроет .child-a целиком */
```

`.child-a` никогда не окажется выше `.parent-b`, потому что сравнение идёт на уровне `.parent-a` (z-index: 1) против `.parent-b` (z-index: 2).

> Проверить контексты можно в DevTools → вкладка "Layers" (Chrome).
