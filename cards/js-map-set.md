---
id: js-map-set
category: Frontend
daily: true
---

# Чем Map и Set отличаются от Object и Array в JavaScript?

## Ответ

**Map** — коллекция пар ключ-значение, где ключом может быть **любой тип** (не только строка, как в Object), и порядок вставки всегда сохраняется.

```js
const map = new Map();
map.set('name', 'Alex');
map.set(42, 'числовой ключ');
map.set({ id: 1 }, 'объект как ключ');

map.get('name');   // 'Alex'
map.size;           // 3
map.has(42);         // true
map.delete(42);

for (const [key, value] of map) {
  console.log(key, value);
}
```

**Set** — коллекция **уникальных** значений (дубликаты автоматически отбрасываются).

```js
const set = new Set([1, 2, 2, 3, 3, 3]);
set.size;        // 3 → { 1, 2, 3 }

set.add(4);
set.has(2);        // true
set.delete(1);

// Частый приём: убрать дубликаты из массива
const unique = [...new Set([1, 1, 2, 2, 3])]; // [1, 2, 3]
```

| | `Object` | `Map` |
|---|---|---|
| Ключи | только строки/символы | любой тип |
| Порядок | не гарантирован (для не-числовых ключей — да, но неявно) | всегда порядок вставки |
| Размер | `Object.keys(obj).length` | `map.size` |
| Итерация | нужен `Object.entries()` | напрямую `for...of` |

Используйте `Map`/`Set`, когда ключи не строковые, важен порядок или нужен быстрый `.size`.
