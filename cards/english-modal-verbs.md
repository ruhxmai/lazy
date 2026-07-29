---
id: english-modal-verbs
category: English
daily: true
---

# Как правильно использовать should/would/could в код-ревью и обсуждениях?

## Ответ

Модальные глаголы делают фидбек **вежливым и не категоричным** — это важно в код-ревью, где прямое "you are wrong" звучит грубо.

**`should`** — рекомендация, "стоило бы":

```
This function should handle the empty array case.
Maybe you should extract this into a separate helper.
```

**`could`** — мягкое предложение, один из вариантов:

```
We could use a Map here instead of an object for better lookup performance.
You could rename this variable to something more descriptive.
```

**`would`** — гипотетическое действие или вежливая просьба:

```
It would be better to validate the input before saving.
Would you mind adding a test for this edge case?
```

**Прошедшее время — частая ошибка юниоров:**

```
❌ I should to fix this bug yesterday.
✅ I should have fixed this bug yesterday.   (не сделал, хотя должен был)

❌ You could to use useMemo here.
✅ You could have used useMemo here.         (была возможность, не использовал)
```

После модального глагола **никогда не ставится `to`**: `should fix`, не `should to fix`.

**Сравнение вежливости в комментариях к PR:**

| Прямо | Вежливее |
|---|---|
| Fix this. | This should probably be fixed. |
| Use async/await. | You could use async/await instead. |
| Add tests. | It would be good to add tests for this case. |
