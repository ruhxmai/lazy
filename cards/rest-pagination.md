---
id: rest-pagination
category: Backend
daily: true
---
# Какие паттерны пагинации существуют в REST API?
## Ответ
Три основных подхода:

**Offset/Limit** — простой, но медленный на больших объёмах:
```
GET /posts?limit=10&offset=20
```

**Page/Per-page** — удобен для UI с кнопками страниц:
```
GET /posts?page=3&per_page=10
```

**Cursor** — быстрый и стабильный для бесконечных лент:
```
GET /posts?cursor=eyJpZCI6MTAwfQ==&limit=10
```

Ответ содержит мета-информацию:
```json
{ "data": [...], "meta": { "total": 500, "next_cursor": "abc" } }
```

Cursor-пагинация не «съезжает» при добавлении новых записей — предпочтительна для real-time данных.
