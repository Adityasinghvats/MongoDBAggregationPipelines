- What is the average no. of tags per user
```javascript
//learn to work with arrays in aggregation
//unwind - create doc copies with different elements of array
[
  {
    $unwind: "$tags"
  },
  {
    $group: {
      _id: "$_id",
      numberOfTags:{
        $sum:1
      }
    }
  },
  {
    $group: {
      _id: null,
      avgNoOfTags:{
        $avg: "$numberOfTags"
      }
    }
  }
]
```
```javascript
[
  {
    $addFields: {
      numberOfTags:{
        $size: {$ifNull:[ "$tags", []]}
      }
    }
  },
  {
    $group: {
      _id: null,
      avgNoOfTags:{
        $avg: "$numberOfTags"
      }
    }
  }
```