- Find total no. of males and females
```javascript
[
  {
    $group: {
      _id: "$gender",
      genderCount:{
        $sum : 1
      }
    }
  }
]
```
- Which country has highest no. of registered users
```javascript
[
  {
    $group: {
      _id: "$company.location.country",
      count:{
        $sum: 1
      }
    }
  },
  {
    $sort: {
      count: -1
    }
  },
  {
    $limit: 1
  }
]
```
- List all unique eye colors
```javascript
[
  {
    $group: {
      _id: "$eyeColor",
      count: {
        $sum: 1,
      },
    },
  },
]
```