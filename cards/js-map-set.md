---
id: js-map-set
category: JavaScript
daily: true
---

# Чем Map и Set отличаются от Object и Array в JavaScript?

## Ответ

**Map** — коллекция пар ключ-значение, где ключом может быть **любой тип** (объект, функция, число), а не только строка/символ, как в `Object`. Порядок ключей всегда соответствует порядку добавления, есть свойство `size`.

```js
const map = new Map();
const userKey = { id: 1 };

map.set(userKey, "Alice");
map.set("role", "admin");

map.get(userKey);   // "Alice"
map.size;           // 2
map.has("role");    // true
map.delete("role");

for (const [key, value] of map) {
  console.log(key, value);
}
```

**Set** — коллекция **уникальных значений** любого типа (аналог массива без дублей).

```js
const set = new Set([1, 2, 2, 3]);
set.add(4);
set.has(2);       // true
set.size;         // 4

// Быстрый способ убрать дубли из массива
const unique = [...new Set([1, 1, 2, 3, 3])]; // [1, 2, 3]
```

| Критерий | Object | Map | Array | Set |
|---|---|---|---|---|
| Ключи | строка/символ | любой тип | числовой индекс | — |
| Порядок | не гарантирован (ES2015+ почти всегда) | гарантирован | гарантирован | гарантирован |
| Размер | `Object.keys(obj).length` | `.size` | `.length` | `.size` |
| Дубли значений | — | — | допустимы | запрещены |

> На практике: `Map`/`Set` быстрее для частых добавлений/удалений и не имеют риска коллизий с встроенными свойствами прототипа (`toString`, `hasOwnProperty`).
