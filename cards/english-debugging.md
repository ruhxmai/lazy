---
id: english-debugging
category: English
daily: true
---
# Как описать баг на английском в issue или в чате?
## Ответ
Стандартная структура баг-репорта:

| Раздел | Фраза |
|---|---|
| Шаги воспроизведения | `Steps to reproduce:` |
| Ожидаемый результат | `Expected behavior:` |
| Фактический результат | `Actual behavior:` |
| Среда | `Environment: Chrome 124, Node 20` |
| Блокер | `This is blocking our release.` |
| Причина | `Root cause: ...` |
| Исправлено | `Fixed in commit abc123.` |

Пример:
```
Bug: Login button does nothing when form is empty.
Steps to reproduce:
  1. Open /login
  2. Click Submit without filling the form
Expected: show validation error
Actual: nothing happens
```
