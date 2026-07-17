---
id: sql-isolation-levels
category: Backend
difficulty: junior
daily: true
---

# Какие уровни изоляции транзакций есть в SQL?

## Ответ

Уровень изоляции определяет, насколько параллельные транзакции «видят» изменения друг друга — компромисс между консистентностью и производительностью.

| Уровень | Dirty read | Non-repeatable read | Phantom read |
|---|---|---|---|
| `READ UNCOMMITTED` | возможен | возможен | возможен |
| `READ COMMITTED` | нет | возможен | возможен |
| `REPEATABLE READ` | нет | нет | возможен* |
| `SERIALIZABLE` | нет | нет | нет |

*в PostgreSQL `REPEATABLE READ` фактически защищает и от фантомных чтений, в отличие от стандарта SQL.

```sql
BEGIN TRANSACTION ISOLATION LEVEL SERIALIZABLE;

SELECT balance FROM accounts WHERE id = 1;
UPDATE accounts SET balance = balance - 100 WHERE id = 1;

COMMIT;
```

**Термины:**
- **Dirty read** — чтение незакоммиченных изменений другой транзакции
- **Non-repeatable read** — повторный `SELECT` той же строки в транзакции даёт другой результат
- **Phantom read** — повторный `SELECT` с условием возвращает другой **набор строк** (появились/исчезли)

По умолчанию в PostgreSQL и Oracle — `READ COMMITTED`, в MySQL (InnoDB) — `REPEATABLE READ`. Чем строже уровень, тем больше блокировок и ниже пропускная способность под нагрузкой.
