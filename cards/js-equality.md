---
id: js-equality
category: Frontend
difficulty: junior
daily: true
---

# Чем отличается == от === в JavaScript?

## Ответ

`===` сравнивает значение и тип, без преобразования (strict equality). `==` сначала приводит типы (type coercion), потом сравнивает.

```js
1 == '1';   // true  — строка приводится к числу
1 === '1';  // false — разные типы

null == undefined;  // true
null === undefined; // false

0 == false; // true
0 === false; // false
```

Практическое правило: **всегда используйте `===`**, кроме `== null` для проверки на `null` и `undefined` одновременно.

```js
if (value == null) { /* true для null и undefined */ }
```
