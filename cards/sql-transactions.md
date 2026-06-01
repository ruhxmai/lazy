---
id: sql-transactions
category: Backend
daily: true
---

# Что такое транзакция в SQL и что означает ACID?

## Ответ

Транзакция — группа SQL-операций, выполняемых **атомарно**: либо все, либо ни одна.

```sql
BEGIN;
  UPDATE accounts SET balance = balance - 100 WHERE id = 1;
  UPDATE accounts SET balance = balance + 100 WHERE id = 2;
COMMIT;
-- При ошибке:
ROLLBACK;
```

**ACID** — четыре свойства транзакции:
- **A**tomicity — всё или ничего
- **C**onsistency — данные остаются корректными
- **I**solation — транзакции не мешают друг другу
- **D**urability — после `COMMIT` изменения сохранены навсегда
