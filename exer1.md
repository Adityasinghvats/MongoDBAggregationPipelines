## MongoDB Aggregation Pipelines

- Count no. of active users
 ```javascript
[
  {
    $match: {
      isActive: true,
    },
  },
  {
    $count: "activeUsers",
  },
]
```
- What is a average age of all users
```javascript
[
  {
    $group: {
      //to get entire document
      _id: null,
      averageAge:{
        $avg: "$age"
      }
    }
  }
]
```
- What is a average age of both genders
```javascript
[
  {
    $group: {
      //to get entire document
      _id: "$gender",
      averageAge:{
        $avg: "$age"
      }
    }
  }
]
```
- List the top 5 common fruits among the users
```javascript
[//stage 1
  {
    $group: {
      _id: "$favoriteFruit",
      count:{
        //increment by 1 on finding a person with this fruit preference
        $sum: 1
      }
    },
  },
  //stage 2
  {
    $sort: {
      count: 1
    }
  },
  //stage3-find top k
  {
    $limit: 2
  }
]
```
