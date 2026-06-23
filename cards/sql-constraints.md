---
id: sql-constraints
category: Backend
difficulty: junior
daily: true
---

# Какие ограничения (constraints) бывают в SQL?

## Ответ

Constraints — правила целостности данных, задаваемые на уровне таблицы:

```sql
CREATE TABLE users (
  id       SERIAL       PRIMARY KEY,              -- уникальный + NOT NULL
  email    VARCHAR(255) UNIQUE NOT NULL,           -- уникальный и обязательный
  age      INT          CHECK (age >= 0),          -- только >= 0
  role_id  INT          REFERENCES roles(id)       -- внешний ключ
                        ON DELETE SET NULL,
  name     TEXT         DEFAULT 'Anonymous'        -- значение по умолчанию
);
```

| Constraint | Что делает |
|---|---|
| `PRIMARY KEY` | уникальный идентификатор строки, автоматически NOT NULL |
| `UNIQUE` | значение не повторяется в колонке (NULL допускается) |
| `NOT NULL` | поле обязательно для заполнения |
| `CHECK` | произвольное логическое условие |
| `FOREIGN KEY` / `REFERENCES` | ссылка на строку другой таблицы |
| `DEFAULT` | значение при вставке без указания поля |

`ON DELETE CASCADE` — удаляет дочерние строки при удалении родительской.
`ON DELETE SET NULL` — ставит NULL в дочернем поле.
