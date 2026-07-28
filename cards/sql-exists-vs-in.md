---
id: sql-exists-vs-in
category: Backend
difficulty: junior
daily: true
---

# Чем `EXISTS` отличается от `IN` в SQL-подзапросах?

## Ответ

Оба используются для фильтрации по результату подзапроса, но работают по-разному.

**`IN`** — сравнивает значение колонки со **списком значений**, которые вернул подзапрос:

```sql
SELECT * FROM orders
WHERE user_id IN (SELECT id FROM users WHERE country = 'RU');
```

**`EXISTS`** — проверяет, вернул ли подзапрос **хотя бы одну строку** для каждой строки внешнего запроса, не сравнивая конкретные значения:

```sql
SELECT * FROM orders o
WHERE EXISTS (
  SELECT 1 FROM users u WHERE u.id = o.user_id AND u.country = 'RU'
);
```

| | `IN` | `EXISTS` |
|---|---|---|
| Что возвращает подзапрос | Список значений | Просто факт «есть строки или нет» |
| Производительность на больших подзапросах | Материализует весь список | Обычно быстрее — останавливается на первой найденной строке |
| Поведение с `NULL` в списке | Ломается в `NOT IN` | `NOT EXISTS` работает предсказуемо |

**Частая ловушка junior-разработчика:** `NOT IN` с подзапросом, который может вернуть `NULL`, — весь результат станет пустым:

```sql
-- Если хотя бы один user_id = NULL, весь запрос вернёт 0 строк!
SELECT * FROM orders WHERE user_id NOT IN (SELECT user_id FROM banned_users);

-- Безопаснее — NOT EXISTS, не подвержен этой проблеме
SELECT * FROM orders o
WHERE NOT EXISTS (SELECT 1 FROM banned_users b WHERE b.user_id = o.user_id);
```