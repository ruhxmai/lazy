---
id: sql-transactions
category: Backend
daily: true
---

# Что такое транзакция в SQL?

## Ответ

Транзакция — это **группа SQL-операций**, которые выполняются как одно целое: либо все успешно, либо ни одна.

```sql
BEGIN;

UPDATE accounts SET balance = balance - 100 WHERE id = 1;
UPDATE accounts SET balance = balance + 100 WHERE id = 2;

COMMIT;  -- сохранить все изменения
-- или ROLLBACK; -- откатить всё назад
```

Свойства транзакций описывает **ACID**:
- **A**tomicity — атомарность (всё или ничего)
- **C**onsistency — согласованность
- **I**solation — изолированность
- **D**urability — долговечность
