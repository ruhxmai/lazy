---
id: js-var-let-const
category: Frontend
daily: true
---

# Чем отличаются var, let и const в JavaScript?

## Ответ

**`var`** — область видимости функции (function-scope), поднимается (hoisting) с инициализацией `undefined`, можно переобъявлять.

**`let`** — область видимости блока (block-scope), попадает в **Temporal Dead Zone** до объявления, переобъявление в том же блоке запрещено.

**`const`** — как `let`, но переприсвоение переменной запрещено. Объект, на который она ссылается, всё ещё можно мутировать.

```js
console.log(a); // undefined (hoisting)
var a = 1;

console.log(b); // ReferenceError (TDZ)
let b = 2;

const obj = { x: 1 };
obj.x = 2;      // OK — мутация объекта
obj = {};       // TypeError — переприсвоение

for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i)); // 3, 3, 3 — одна общая переменная
}
for (let j = 0; j < 3; j++) {
  setTimeout(() => console.log(j)); // 0, 1, 2 — своя переменная на итерацию
}
```

> На практике: используй `const` по умолчанию, `let` — когда переменная переприсваивается, `var` — почти никогда.
