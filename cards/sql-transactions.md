---
id: sql-transactions
category: Backend
daily: true
---
# Что такое транзакция в SQL и ACID-свойства?
## Ответ
**Транзакция** — набор SQL-операций, выполняемых как единое целое. Если одна операция падает — все изменения откатываются.

**ACID:**
| Свойство | Что означает |
|---|---|
| Atomicity | Всё или ничего |
| Consistency | БД остаётся в корректном состоянии |
| Isolation | Транзакции не видят незавершённые изменения друг друга |
| Durability | После COMMIT данные сохранены навсегда |

```sql
BEGIN;
  UPDATE accounts SET balance = balance - 100 WHERE id = 1;
  UPDATE accounts SET balance = balance + 100 WHERE id = 2;
COMMIT;
-- При ошибке:
ROLLBACK;
```
