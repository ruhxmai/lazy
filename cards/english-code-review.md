---
id: english-code-review
category: English
daily: true
---
# Какие фразы используют при code review на английском?
## Ответ
Стандартные маркеры в комментариях:

- **Nit:** — мелкое незначительное замечание: *"Nit: rename this variable for clarity"*
- **LGTM** — Looks Good To Me (одобрение PR)
- **Blocking** / **Non-blocking** — блокирует ли замечание мёрж: *"Blocking: this will cause a null pointer"*
- **Could you…?** — вежливая просьба: *"Could you add a test for this edge case?"*
- **Out of scope** — *"This refactor is out of scope, let's track it separately"*
- **Consider** — мягкое предложение: *"Consider extracting this into a helper function"*
- **As discussed** — ссылка на договорённость из обсуждения
