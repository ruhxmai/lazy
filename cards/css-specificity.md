---
id: css-specificity
category: Frontend
difficulty: junior
daily: true
---

# Как считается специфичность (specificity) CSS-селекторов?

## Ответ

Специфичность определяет, какое правило победит при конфликте. Считается весом по 4 категориям (по убыванию приоритета):

```
inline style  >  ID          >  class/attribute/pseudo-class  >  element/pseudo-element
  (1,0,0,0)     (0,1,0,0)              (0,0,1,0)                       (0,0,0,1)
```

```css
#header { color: red; }        /* (0,1,0,0) */
.nav .link { color: blue; }    /* (0,0,2,0) */
div { color: green; }          /* (0,0,0,1) */
```

`#header` победит `.nav .link`, потому что один ID весит больше двух классов. `!important` перебивает всё — используйте редко, усложняет поддержку.
