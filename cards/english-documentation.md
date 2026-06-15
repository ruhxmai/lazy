---
id: english-documentation
category: English
daily: true
---
# Как писать технические комментарии по-английски?
## Ответ
Используй краткие глаголы в форме настоящего времени или повелительном наклонении:

```js
// Returns the user's full name.
// Throws if id is null or undefined.
// Deprecated: use getUserById() instead.
// TODO: handle edge case when array is empty.
// FIXME: race condition on concurrent writes.
// NOTE: this relies on browser-only APIs.
```

Полезные фразы: *This function...*, *Note that...*, *See also:*, `@param`, `@returns`, `@throws`.
