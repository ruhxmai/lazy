---
id: english-changelog
category: English
daily: true
---

# Present Perfect или Past Simple в changelog и pull request?

## Ответ

Для changelog/release notes используется **Present Perfect** (has/have + V3) — акцент на результате, важном сейчас:

```
## v2.3.0
- Fixed a bug where login button was unresponsive
- Added pagination to the user list
- Improved performance of the search endpoint
```

Заголовки записей начинаются с **глагола в форме Past Participle** (Fixed, Added, Improved), а не с инфинитива — в отличие от заголовков задач (issue titles), где используется инфинитив.

```
Issue title:   Add dark mode support                (инфинитив)
Changelog:     Added dark mode support               (Past Participle)
Commit body:   This commit adds dark mode support     (Present Simple, описательно)
```
