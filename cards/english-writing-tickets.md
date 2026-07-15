---
id: english-writing-tickets
category: English
difficulty: junior
daily: true
---

# Как правильно описать баг в тикете на английском?

## Ответ

Хороший баг-репорт отвечает на три вопроса: что ты сделал, что ожидал и что получил на самом деле.

**Структура:**

> **Steps to reproduce:**
> 1. Go to the login page
> 2. Enter valid credentials and click "Sign in"
>
> **Expected result:** The user is redirected to the dashboard.
>
> **Actual result:** The page stays blank and the console shows a 500 error.
>
> **Environment:** Chrome 126, staging.

**Полезные фразы:**
- `steps to reproduce` — шаги для воспроизведения
- `expected vs actual behavior` — ожидаемое и фактическое поведение
- `it fails silently` — падает без видимой ошибки
- `intermittently / consistently` — периодически / постоянно (воспроизводится)
- `attached a screenshot / log` — приложил скриншот / лог
- `blocking` / `not a blocker` — блокирует релиз / не критично
