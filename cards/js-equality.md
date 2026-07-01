---
id: js-equality
category: Frontend
difficulty: junior
daily: true
---

# Чем отличается == от === в JavaScript?

## Ответ

`===` сравнивает **без приведения типов** (строгое сравнение), `==` сначала приводит операнды к одному типу.

```js
1 == '1';   // true  (строка приводится к числу)
1 === '1';  // false (разные типы)

null == undefined;  // true
null === undefined; // false

0 == false;  // true
0 === false; // false

NaN === NaN; // false — NaN не равен даже самому себе
```

Правило: всегда используйте `===` и `!==`, кроме случая `x == null` — это одна проверка сразу на `null` и `undefined`.
