---
id: sql-n-plus-one
category: Backend
daily: true
---

# Что такое проблема N+1 запросов и как её избежать?

## Ответ

**N+1 problem** — антипаттерн, когда код делает **1 запрос** за списком записей, а затем **ещё N запросов** — по одному на каждую запись, чтобы получить связанные данные. Итого N+1 обращений к базе вместо одного-двух.

```js
// 1 запрос: получить всех авторов
const authors = await db.query("SELECT * FROM authors");

// N запросов: для каждого автора — отдельный запрос книг
for (const author of authors) {
  author.books = await db.query(
    "SELECT * FROM books WHERE author_id = ?", [author.id]
  ); // выполняется authors.length раз!
}
```

При 100 авторах это 101 запрос вместо 1-2 — резкое падение производительности, особенно с сетевой задержкой до БД.

**Решение 1 — JOIN одним запросом:**

```sql
SELECT authors.*, books.*
FROM authors
LEFT JOIN books ON books.author_id = authors.id;
```

**Решение 2 — batch-запрос с IN:**

```js
const authors = await db.query("SELECT * FROM authors");
const ids = authors.map(a => a.id);
const books = await db.query(
  "SELECT * FROM books WHERE author_id IN (?)", [ids]
); // всего 2 запроса вместо N+1
// далее books группируются по author_id в памяти
```

**Решение 3 — eager loading в ORM** (Prisma `include`, Sequelize `include`, TypeORM `relations`) — ORM сам построит JOIN или batch-запрос вместо запроса в цикле.

> Инструмент диагностики: логирование SQL-запросов в dev-режиме или APM (New Relic, Sentry) — N+1 сразу виден как всплеск одинаковых запросов подряд.
