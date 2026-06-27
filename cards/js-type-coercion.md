---
id: js-type-coercion
category: JavaScript
daily: true
---
# В чём разница между == и === в JavaScript?
## Ответ
`==` сравнивает значения **с приведением типов**, `===` — **без приведения** (строгое равенство).

```js
0 == '0'          // true  ('0' → 0)
0 === '0'         // false (разные типы)
null == undefined  // true
null === undefined // false
NaN == NaN        // false (NaN никогда не равен себе)
```

**Falsy-значения** (приводятся к `false`):
`false`, `0`, `''`, `null`, `undefined`, `NaN`

**Правило:** всегда используй `===` — явное лучше неявного.
