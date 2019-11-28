# Chapter 1: Basic Aggregation - $match and $project
## Lab - $match
**Question**

Help MongoDB pick a movie our next movie night! Based on employee polling, we've decided that potential movies must meet the following criteria.

- imdb.rating is at least 7
- genres does not contain "Crime" or "Horror"
- rated is either "PG" or "G"
- languages contains "English" and "Japanese"

Assign the aggregation to a variable named pipeline, like:

```
var pipeline = [ { $match: { ... } } ]
```

- As a hint, your aggregation should return 23 documents. You can verify this by typing db.movies.aggregate(pipeline).itcount()
- Load validateLab1.js into mongo shell

```
load('validateLab1.js')
```

- And run the validateLab1 validation method

```
validateLab1(pipeline)
```

What is the answer?

**Answer**

15.

## Lab - Changing Document Shape with $project
**Question**

Our first movie night was a success. Unfortunately, our ISP called to let us know we're close to our bandwidth quota, but we need another movie recommendation!

Using the same $match stage from the previous lab, add a $project stage to only display the the title and film rating (title and rated fields).

- Assign the results to a variable called pipeline.

```
var pipeline = [{ $match: {. . .} }, { $project: { . . . } }]
```

- Load validateLab2.js which was included in the same handout as validateLab1.js and execute validateLab2(pipeline)?

```
load('./validateLab2.js')
```

- And run the validateLab2 validation method

```
validateLab2(pipeline)
```

What is the answer?

**Answer**

15.
