# Chapter 2: The MongoDB Query Language + Atlas

## Lab 2.1: How Many Comedies?

**Question**

How many documents in video.movieDetails match the filter {genres: "Comedy"}?

**Answer**

749.

## Lab 2.2: How Many Inserted?

**Question**

If the collection video.myMovies is currently empty, how many documents would be inserted by the following call to insertMany().

```
db.myMovies.insertMany(
  [
    {
      "_id" : "tt0084726",
      "title" : "Star Trek II: The Wrath of Khan",
      "year" : 1982,
      "type" : "movie"
    },
    {
      "_id" : "tt0796366",
      "title" : "Star Trek",
      "year" : 2009,
      "type" : "movie"
    },
    {
      "_id" : "tt0084726",
      "title" : "Star Trek II: The Wrath of Khan",
      "year" : 1982,
      "type" : "movie"
    },
    {
      "_id" : "tt1408101",
      "title" : "Star Trek Into Darkness",
      "year" : 2013,
      "type" : "movie"
    },
    {
      "_id" : "tt0117731",
      "title" : "Star Trek: First Contact",
      "year" : 1996,
      "type" : "movie"
    }
  ],
  {
    ordered: false
  }
);
```

**Answer**

4.

## Lab 2.3: Queries on Scalar Fields

**Question**

Explore the movieDetails collection that you loaded into your Atlas sandbox cluster and then issue a query to answer the following question. How many movies in the movieDetails collection are rated PG and have exactly 10 award nominations?

You will find the count() method useful in answering this question using the mongo shell.

**Answer**

3.

## Lab 2.4: Queries on Array Fields, Part 1

**Question**

Explore the movieDetails collection that you loaded into your Atlas sandbox cluster and then issue a query to answer the following question. How many movies in the movieDetails collection list "Family" among its genres?

You will find the count() method useful in answering this question using the mongo shell.

**Answer**

124.

## Lab 2.5: Queries on Array Fields, Part 2

**Question**

Explore the movieDetails collection that you loaded into your Atlas sandbox cluster and then issue a query to answer the following question. How many movies in the movieDetails collection list "Western" second among its genres?

You will find the count() method useful in answering this question using the mongo shell.

**Answer**

14.

## Lab 2.6: Update Operators

**Question**

Suppose you wish to update the value of the plot field for one document in our movieDetails collection to correct a typo. Which of the following update operators and modifiers would you need to use to do this?

**Answer**

\$set.
