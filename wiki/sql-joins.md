---
title: SQL JOINs
category: Backend
---

# SQL JOINs

JOIN — оператор SQL, объединяющий строки из двух и более таблиц на основании связанных колонок. Это один из фундаментальных инструментов работы с реляционными базами данных.

## Типы JOIN

### INNER JOIN
Возвращает только строки, у которых есть совпадение **в обеих** таблицах.

```sql
SELECT users.name, orders.total
FROM users
INNER JOIN orders ON users.id = orders.user_id;
-- Пользователи без заказов НЕ попадут в результат
```

### LEFT JOIN (LEFT OUTER JOIN)
Возвращает **все** строки из левой таблицы и совпадающие из правой. Где совпадения нет — `NULL`.

```sql
SELECT users.name, orders.total
FROM users
LEFT JOIN orders ON users.id = orders.user_id;
-- Пользователи без заказов попадут, orders.total = NULL
```

### RIGHT JOIN
Зеркало LEFT JOIN — все строки из правой таблицы.

### FULL OUTER JOIN
Все строки из обеих таблиц. Где нет совпадения — `NULL` со стороны, в которой нет записи.

```sql
SELECT * FROM a
FULL OUTER JOIN b ON a.id = b.a_id;
```

### CROSS JOIN
Декартово произведение: каждая строка левой таблицы соединяется с каждой строкой правой.

```sql
SELECT * FROM colors CROSS JOIN sizes;
-- 3 цвета × 4 размера = 12 строк
```

## Схема

```mermaid
flowchart LR
    subgraph tables["Исходные таблицы"]
        U[(users\nid | name)]
        O[(orders\nid | user_id | total)]
    end

    subgraph joins["Результаты JOIN"]
        IJ["INNER JOIN\nтолько совпадения"]
        LJ["LEFT JOIN\nвсе users + совпадения"]
        FJ["FULL OUTER JOIN\nвсе строки обеих таблиц"]
    end

    U -->|ON users.id = orders.user_id| IJ
    O -->|ON users.id = orders.user_id| IJ
    U -->|все строки| LJ
    O -.->|NULL если нет| LJ
    U -->|все строки| FJ
    O -->|все строки| FJ
```

## Производительность и индексы

Индексы на колонках JOIN критически важны для больших таблиц:

```sql
-- Создать индекс на колонке связи
CREATE INDEX idx_orders_user_id ON orders(user_id);

-- Проверить план запроса
EXPLAIN SELECT users.name, orders.total
FROM users
INNER JOIN orders ON users.id = orders.user_id
WHERE orders.total > 100;
```

Если в EXPLAIN видишь `Seq Scan` вместо `Index Scan` на большой таблице — нужен индекс.

## Частые ошибки

- Путать INNER и LEFT JOIN — теряются строки без совпадений
- JOIN без индекса на колонке связи — медленный full table scan
- Несколько LEFT JOIN подряд без осознания — декартово произведение при ошибке в условии

## Карточки
- Чем INNER JOIN отличается от LEFT JOIN?
- Что вернёт LEFT JOIN, если в правой таблице нет совпадения?
- Зачем нужен индекс на колонке, используемой в JOIN?
- Что такое CROSS JOIN и когда он применяется?
- Как проверить, использует ли запрос индекс?
