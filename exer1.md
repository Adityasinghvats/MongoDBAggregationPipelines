## MongoDB Aggregation Pipelines

- Count no. of active users
 ```json
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
```json
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
```json
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
```json
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