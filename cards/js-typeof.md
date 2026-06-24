---
id: js-typeof
category: Frontend
daily: true
---

# Что возвращает typeof и как работает приведение типов в JS?

## Ответ

`typeof` возвращает строку с именем типа значения.

```js
typeof 42           // "number"
typeof "hello"      // "string"
typeof true         // "boolean"
typeof undefined    // "undefined"
typeof null         // "object" ← исторический баг
typeof {}           // "object"
typeof []           // "object"
typeof function(){} // "function"
typeof Symbol()     // "symbol"

// Неявное приведение типов (coercion)
"5" + 1   // "51" — число стало строкой
"5" - 1   // 4   — строка стала числом
!!0       // false
!!"text"  // true
```

Для проверки массива используй `Array.isArray(val)`, а не `typeof`.
