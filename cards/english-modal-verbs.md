---
id: english-modal-verbs
category: English
difficulty: junior
daily: true
---

# Как использовать модальные глаголы (should/could/would/might) в code review и обсуждениях?

## Ответ

Модальные глаголы задают **тон вежливости и уверенности** — важно в код-ревью, чтобы не звучать резко.

| Глагол   | Смысл                          | Пример                                            |
|----------|---------------------------------|----------------------------------------------------|
| `should` | рекомендация, совет            | "This function **should** handle the null case."   |
| `could`  | мягкое предложение, вариант    | "You **could** extract this into a helper."        |
| `would`  | гипотетическое, вежливая просьба | "**Would** it make sense to memoize this?"        |
| `might`  | осторожное предположение       | "This **might** cause a race condition."           |
| `must`   | жёсткое требование (редко в ревью) | "This **must** not log secrets."                |

Сравните тон:

```
❌ "This is wrong. Fix it."
✅ "This might break when the array is empty — could we add a check?"

❌ "You need to use useMemo here."
✅ "This would probably be faster with useMemo."
```

`could`/`would`/`might` смягчают комментарий и превращают критику в предложение — это стандарт вежливого код-ревью в англоязычных командах. `must`/`need to` оставляют для действительно критичных вещей (security, баги в проде).
