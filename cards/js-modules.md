---
id: js-modules
category: JavaScript
difficulty: junior
daily: true
---

# Чем отличается default export от named export?

## Ответ

**Named export** — именованный экспорт, таких в файле может быть несколько:

```js
// math.js
export const add = (a, b) => a + b;
export const sub = (a, b) => a - b;

// Импорт — имена должны совпадать (или псевдоним через as)
import { add, sub } from './math.js';
import { add as plus } from './math.js';
```

**Default export** — экспорт по умолчанию, только один на файл:

```js
// Button.jsx
export default function Button({ label }) {
  return <button>{label}</button>;
}

// Импорт — имя можно задать любое
import Button from './Button.jsx';
import MyBtn from './Button.jsx'; // тоже работает
```

**Когда что использовать:**
- Компоненты React → default export
- Утилиты, константы, хуки → named export
- Смешивать в одном файле можно, но лучше не злоупотреблять
