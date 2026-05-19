---
id: english-naming
category: English
daily: true
---
# Какие naming conventions используются в разработке?

## Ответ
| Стиль | Пример | Где используется |
|---|---|---|
| camelCase | `getUserName` | JS переменные, функции |
| PascalCase | `UserProfile` | JS классы, React компоненты |
| snake_case | `user_name` | Python, SQL, Ruby |
| kebab-case | `user-profile` | CSS классы, URL, HTML атрибуты |
| SCREAMING_SNAKE_CASE | `MAX_RETRY_COUNT` | Константы |

```js
const MAX_SIZE = 100;         // SCREAMING_SNAKE — константа
class UserService {}           // PascalCase — класс
function fetchUserData() {}    // camelCase — функция
```

В JS нельзя использовать kebab-case для переменных — это синтаксическая ошибка.
