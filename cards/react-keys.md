---
id: react-keys
category: Frontend
daily: true
---
# Зачем React нужны `key` в списках?
## Ответ
`key` — уникальный идентификатор элемента списка. React использует его при reconciliation (сверке): вместо перерендера всего списка он понимает, какие элементы добавились, удалились или переместились.

**Плохо:** индекс массива как key (баги при сортировке/удалении).  
**Хорошо:** стабильный уникальный `id` из данных.

```jsx
// Bad — index breaks reorder/delete
items.map((item, index) => <li key={index}>{item.name}</li>)

// Good — stable id
items.map(item => <li key={item.id}>{item.name}</li>)
```
