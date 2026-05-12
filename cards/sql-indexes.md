---
id: sql-indexes
category: Backend
difficulty: junior
daily: true
---

# Что такое индекс в SQL и зачем он нужен?

## Ответ

Индекс — структура данных (обычно B-tree), которая позволяет базе **быстро находить строки** без полного перебора таблицы (full scan).

```sql
-- Создать индекс по полю email
CREATE INDEX idx_users_email ON users(email);

-- Теперь этот запрос использует индекс — работает быстро
SELECT * FROM users WHERE email = 'test@example.com';
```

**Плюс:** ускоряет `SELECT` по индексированным полям.  
**Минус:** замедляет `INSERT`/`UPDATE`/`DELETE` и занимает место на диске.  
Создавай индексы только для полей, которые часто используются в `WHERE` и `JOIN`.
