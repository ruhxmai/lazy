---
id: sql-n-plus-one
category: Backend
difficulty: junior
daily: true
---

# Что такое проблема N+1 запросов?

## Ответ

Это ситуация, когда для получения связанных данных выполняется **1 запрос на список + N запросов** — по одному на каждую строку — вместо одного объединённого запроса.

```js
// ❌ N+1: 1 запрос на посты + N запросов на авторов
const posts = await db.query('SELECT * FROM posts');
for (const post of posts) {
  post.author = await db.query('SELECT * FROM users WHERE id = ?', [post.authorId]);
}
```

```sql
-- ✅ Один запрос через JOIN
SELECT posts.*, users.name AS author_name
FROM posts
JOIN users ON users.id = posts.author_id;
```

Решения: `JOIN`, batching (`WHERE id IN (...)`), eager loading в ORM (`include`, `populate`, `select_related`).
