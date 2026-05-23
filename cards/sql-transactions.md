---
id: sql-transactions
category: Backend
difficulty: junior
daily: true
---

# Что такое транзакция в SQL и что означает ACID?

## Ответ

Транзакция — группа SQL-операций, которые выполняются как одно целое: либо все, либо ни одна.

```sql
BEGIN;

UPDATE accounts SET balance = balance - 1000 WHERE id = 1;
UPDATE accounts SET balance = balance + 1000 WHERE id = 2;

COMMIT;  -- фиксируем изменения
-- или ROLLBACK;  -- отменяем всё
```

**ACID — 4 свойства транзакции:**

| Свойство | Значение |
|----------|----------|
| **A**tomicity | Всё или ничего |
| **C**onsistency | БД остаётся в корректном состоянии |
| **I**solation | Транзакции не мешают друг другу |
| **D**urability | После COMMIT данные сохранены навсегда |

- Без транзакций перевод денег может прерваться на середине
- `ROLLBACK` откатывает все изменения в рамках транзакции
