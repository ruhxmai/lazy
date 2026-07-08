---
id: english-false-friends
category: English
daily: true
---

# Какие английские слова — «ложные друзья переводчика» — путают разработчиков?

## Ответ

Слова, похожие на русские по звучанию, но с другим значением:

```
actual        — реальный, фактический      (НЕ "актуальный" → current/relevant)
eventually    — в конце концов, со временем (НЕ "возможно" → possibly)
sympathetic   — сочувствующий               (НЕ "симпатичный" → nice/cute)
accurate      — точный                      (НЕ "аккуратный" → tidy/neat)
fabric        — ткань                       (НЕ "фабрика" → factory/plant)
replica       — точная копия                (НЕ "реплика" в смысле фразы → line/remark)
intelligence  — интеллект, разведка         (НЕ "интеллигенция" → intelligentsia)
list          — список                      (НЕ "лист" бумаги → sheet)
magazine      — журнал                      (НЕ "магазин" → store/shop)
```

**Пример в контексте код-ревью:**

```
"The actual bug is in the auth middleware, not the DB layer."
→ Настоящая (фактическая) проблема — в auth middleware, а не в слое БД.
```

> Ложные друзья особенно опасны в PR-описаниях и багрепортах — неверное слово меняет смысл отчёта об ошибке.
