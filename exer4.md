- How many users have 'enim' as their tag
```javascript
[
  {
    $match: {
      tags:"enim"
    }
  },
  {
    $count:'usersWIthEnimTag'
  }
]
```
- What are the names and age of the users who are inactive and have 'velit' as the tag
```javascript
[
  {
    $match: {
      tags: "velit",
      isActive: false,
    },
  },
  {
    $project: {
      name: 1,
      age: 1,
    },
  },
]
```
- How many users have number starting with +1 (940)
```javascript
[
  {
    $match: {
      "company.phone": /^\+1 \(940\)/
    },
  },
  {
    $count: 'peopleWithNo +1(940)'
  }
]
```