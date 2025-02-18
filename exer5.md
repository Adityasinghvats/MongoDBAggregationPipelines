- Who has registered most recently?
``` javascript
[
  {
    $sort: {
      registered: -1
    }
  },
  {
    $limit: 5
  },
  {
    $project: {
      name: 1,
      registered:1,
      favoriteFruit:1
    }
  }
]
```
- Categorize users by favorite fruit
```javascript
[
  {
    $group: {
      _id: "$favoriteFruit",
      users: {
        //The $push operator appends a specified value to an array.
        $push: "$name"
      }
    }
  }
]
```
- How many user have tag 'ad' as the second tag in their list of tags
```javascript
[
  {
    $match: {
      //match second index of array for 'ad'
      "tags.1": "ad"
    }
  },
  {
    $count: 'User with tag ad'
  }
]
```
- Find users who have both 'enim' and 'ad' as their tags
```javascript
[
  {
    $match: {
      tags: {
        $all: ["ad", "enim"],
        },
    }
  },
  {
    $count: 'User with tag ad and enim'
  }
]
```
- List all the companies located in the USA along with all the corresponding user count
```javascript
[
  {
    $match: {
      "company.location.country": "USA",
    },
  },
  {
    $group: {
      _id: "$company.title",
      userCount: {
        $sum: 1,
      },
    },
  },
]
```