---
id: english-bug-report
category: English
difficulty: junior
daily: true
---

# Как правильно описать баг на английском в тикете/issue?

## Ответ

Хороший баг-репорт отвечает на 4 вопроса: что сделал, что ожидал, что получил, в каком окружении.

**Структура:**

```
**Steps to reproduce:**
1. Go to the settings page
2. Click "Save"

**Expected behavior:**
The form should save and show a success message.

**Actual behavior:**
The page throws a 500 error and no data is saved.

**Environment:**
Chrome 126, staging, macOS 14
```

**Полезные фразы:**
- `steps to reproduce` — шаги воспроизведения
- `expected vs actual behavior` — ожидаемое vs фактическое поведение
- `it fails silently` — падает без ошибки/сообщения
- `this happens intermittently` — происходит время от времени
- `a workaround is to...` — обходной путь — это...
- `this is blocking me` — это меня блокирует
- `can you take a look when you get a chance?` — можешь посмотреть, когда будет время?

Избегайте расплывчатого `"it doesn't work"` — уточняйте, **как именно** не работает.
