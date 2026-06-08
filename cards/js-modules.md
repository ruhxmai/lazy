---
id: js-modules
category: Frontend
difficulty: junior
daily: true
---

# Как работают ES6 модули (import / export)?

## Ответ

Модули позволяют разбить код на файлы. Каждый файл — отдельный модуль со своей областью видимости.

```js
// math.js — экспорт
export const PI = 3.14;
export function add(a, b) { return a + b; }
export default function multiply(a, b) { return a * b; }

// main.js — импорт
import multiply, { PI, add } from './math.js';
// default import — без {}, именованный — в {}
```

`export default` — один на файл, при импорте можно использовать любое имя. Именованный `export { name }` — импортируется строго по имени. `import * as math` — импортирует всё как объект.
