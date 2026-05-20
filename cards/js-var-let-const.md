---
id: js-var-let-const
category: Frontend
difficulty: junior
daily: true
---

# В чём разница между var, let и const?

## Ответ

Три способа объявить переменную — с разным поведением по области видимости и поднятию (hoisting).

```js
// var — функциональная область видимости, поднимается
console.log(x); // undefined (не ошибка!)
var x = 5;

// let — блочная область видимости, не поднимается
console.log(y); // ReferenceError
let y = 10;

// const — блочная область видимости, нельзя переназначить
const z = 15;
z = 20; // TypeError

// const с объектом: ссылку нельзя, свойства можно
const user = { name: 'Alice' };
user.name = 'Bob'; // OK
user = {};         // TypeError
```

| Ключевое слово | Область видимости | Hoisting | Переназначение |
|---|---|---|---|
| `var` | функция | да (undefined) | да |
| `let` | блок | нет | да |
| `const` | блок | нет | нет |

- По умолчанию используй `const`, при необходимости переназначить — `let`
- `var` — избегать в современном коде
