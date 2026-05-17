---
id: english-code-comments
category: English
daily: true
---

# Как правильно писать комментарии к коду на английском?

## Ответ

Комментарии пишут на английском — кратко и по делу. Объясняй ПОЧЕМУ, а не ЧТО.

```js
// Bad: очевидно из кода
// increment counter
counter++;

// Good: объясняет причину
// index 0 is reserved for the "unknown" default category
for (let i = 1; i < items.length; i++) { ... }

// TODO — задача на будущее
// TODO: replace with Redis cache when traffic grows

// FIXME — известный баг
// FIXME: race condition when two requests arrive simultaneously

// NOTE — важное замечание
// NOTE: API returns dates in UTC, convert to local time in the UI

// JSDoc для публичных функций
/**
 * Fetches user data by ID.
 * @param {number} id - The user's unique identifier.
 * @returns {Promise<User>} Resolves with the user object.
 */
async function getUser(id) { ... }
```

Полезные глаголы: `handles`, `returns`, `checks whether`, `ensures`, `prevents`, `skips`, `wraps`.
