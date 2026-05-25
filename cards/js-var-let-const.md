---
id: js-var-let-const
category: JavaScript
daily: true
---
# Чем отличаются var, let и const в JavaScript?
## Ответ
`var` имеет функциональную область видимости и поднимается (hoisting) на уровень функции.  
`let` и `const` имеют блочную область видимости (`{}`), не поднимаются аналогично `var`.  
`const` нельзя переприсвоить, но содержимое объекта или массива изменить можно.

```js
function example() {
  var a = 1;   // доступен во всей функции
  let b = 2;   // доступен только в блоке {}
  const c = 3; // нельзя: c = 4
}

if (true) {
  var x = 'var';  // утекает наружу
  let y = 'let';  // только внутри блока
}
console.log(x); // 'var'
console.log(y); // ReferenceError
```
