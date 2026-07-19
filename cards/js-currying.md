---
id: js-currying
category: Frontend
daily: true
---

# Что такое каррирование (currying) в JavaScript?

## Ответ

**Каррирование** — техника, при которой функция с несколькими аргументами превращается в цепочку функций, каждая из которых принимает **один** аргумент.

```js
// Обычная функция
function add(a, b, c) {
  return a + b + c;
}
add(1, 2, 3); // 6

// Каррированная версия
function curryAdd(a) {
  return function (b) {
    return function (c) {
      return a + b + c;
    };
  };
}
curryAdd(1)(2)(3); // 6

// То же самое стрелочными функциями
const curryAdd2 = a => b => c => a + b + c;
```

**Зачем это нужно:**

- **Частичное применение** — можно зафиксировать часть аргументов и переиспользовать функцию:
  ```js
  const add10 = curryAdd(10);
  add10(5)(2); // 17
  ```
- **Композиция функций** — удобно строить пайплайны обработки данных (Redux `connect`, middleware в Express).
- **Переиспользуемые обработчики** в React:
  ```js
  const handleChange = field => event => setForm(prev => ({ ...prev, [field]: event.target.value }));

  <input onChange={handleChange('email')} />
  ```

Каррирование не меняет **что** делает функция — только **как** она принимает аргументы.
