# Chapter 2: MongoDB Indexes

## Lab 2.1: Using Indexes to Sort

**Problem**

In this lab you're going to determine which queries are able to successfully use a given index for both filtering and sorting.

Given the following index:

```
{ "first_name": 1, "address.state": -1, "address.city": -1, "ssn": 1 }
```

Which of the following queries are able to use it for both filtering and sorting?

**Answer**

- [x] db.people.find({ "first_name": "Jessica" }).sort({ "address.state": 1, "address.city": 1 })
- [ ] db.people.find({ "first_name": { \$gt: "J" } }).sort({ "address.city": -1 })
- [x] db.people.find({ "address.state": "South Dakota", "first_name": "Jessica" }).sort({ "address.city": -1 })
- [ ] db.people.find({ "address.city": "West Cindy" }).sort({ "address.city": -1 })
- [x] db.people.find({ "first_name": "Jessica", "address.state": { \$lt: "S"} }).sort({ "address.state": 1 })

## Lab 2.2: Optimizing Compound Indexes

**Problem**

In this lab you're going to examine several example queries and determine which compound index will best service them.

```
> db.people.find({
    "address.state": "Nebraska",
    "last_name": /^G/,
    "job": "Police officer"
  })
```

```
> db.people.find({
    "job": /^P/,
    "first_name": /^C/,
    "address.state": "Indiana"
  }).sort({ "last_name": 1 })
```

```
> db.people.find({
    "address.state": "Connecticut",
    "birthday": {
      "$gte": ISODate("2010-01-01T00:00:00.000Z"),
      "$lt": ISODate("2011-01-01T00:00:00.000Z")
    }
  })
```

If you had to build one index on the people collection, which of the following indexes would best sevice all 3 queries?

**Answer**

```
{ "address.state": 1, "last_name": 1, "job": 1 }
```
