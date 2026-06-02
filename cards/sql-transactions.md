---
id: sql-transactions
category: Backend
daily: true
---
# Что такое транзакция в SQL и зачем она нужна?
## Ответ
Транзакция — группа SQL-операций, которые выполняются **атомарно**: либо все, либо ни одна. Защищает данные от частичных изменений при ошибках.

Принципы **ACID**: Atomicity, Consistency, Isolation, Durability.

```sql
BEGIN;

UPDATE accounts SET balance = balance - 500 WHERE id = 1;
UPDATE accounts SET balance = balance + 500 WHERE id = 2;

-- Если произошла ошибка:
ROLLBACK; -- отменяет обе операции

-- Если всё успешно:
COMMIT;   -- фиксирует обе операции
```

Без транзакции: деньги могут списаться, но не зачислиться.
