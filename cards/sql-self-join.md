---
id: sql-self-join
category: Backend
daily: true
---

# Что такое self join и когда он нужен?

## Ответ

**Self join** — таблица соединяется сама с собой через `JOIN`, используя два разных алиаса. Нужен, когда строки таблицы ссылаются на другие строки той же таблицы.

Классический пример — сотрудники и их менеджеры в одной таблице `employees`:

```sql
SELECT e.name AS employee, m.name AS manager
FROM employees e
LEFT JOIN employees m ON e.manager_id = m.id;
-- employee | manager
-- Alex     | Kate
-- Kate     | NULL   (у CEO нет менеджера)
```

Без алиасов `e` и `m` СУБД не поймёт, к какой "копии" таблицы относится каждая колонка — обязательно нужны два разных имени для одной и той же таблицы.

**Другие частые случаи:** поиск дубликатов, сравнение строк друг с другом (например, товары дороже среднего в своей категории), построение дерева категорий на один уровень.

```sql
-- Найти пары сотрудников из одного отдела
SELECT a.name, b.name, a.department
FROM employees a
JOIN employees b ON a.department = b.department AND a.id < b.id;
```

`LEFT JOIN` в self join часто важнее, чем в обычном — иначе строки без "родителя" (как CEO без менеджера) просто исчезнут из результата.
