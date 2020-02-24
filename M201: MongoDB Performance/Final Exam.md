# Final Exam

## Question 1

**Problem**

Which of these statements is/are true?

**Answer**

- [ ] Write concern has no impact on write latency.
- [ ] You can index multiple array fields in a single document with a single compound index.
- [x] Creating an ascending index on a monotonically increasing value creates index keys on the right-hand side of the index tree.
- [ ] Covered queries can sometimes still require some of your documents to be examined.
- [ ] A collection scan has a logarithmic search time.

## Question 2

**Problem**

Which of the following statements is/are true?

**Answer**

- [x] It's important to ensure that your shard key has high cardinality.
- [x] Indexes can decrease insert throughput.
- [x] Indexes can be walked backwards by inverting their keys in a sort predicate.
- [x] It's important to ensure that secondaries with indexes that differ from the primary not be eligible to become primary.
- [x] Partial indexes can be used to reduce the size requirements of the indexes.

## Question 3

**Problem**

Which of the following statements is/are true?

**Answer**

- [ ] MongoDB indexes are markov trees.
- [x] By default, all MongoDB user-created collections have an _id index.
- [x] It's common practice to co-locate your mongos on the same machine as your application to reduce latency.
- [ ] Background index builds block all reads and writes to the database that holds the collection being indexed.
- [x] Collations can be used to create case insensitive indexes.

## Question 4

**Problem**

Which of the following statements is/are true?

**Answer**

- [ ] On a sharded cluster, aggregation queries using $lookup will require a merge stage on a random shard.
- [x] Indexes are fast to search because they're ordered such that you can find target values with few comparisons.
- [ ] Under heavy write load you should scale your read throughput by reading from secondaries.
- [ ] When you index on a field that is an array it creates a partial index.
- [x] Indexes can solve the problem of slow queries.

## Question 5

**Problem**

Which of the following statements is/are true?

**Answer**

- [ ] By default, the explain() command will execute your query.
- [x] Compound indexes can service queries that filter on a prefix of the index keys.
- [ ] Compound indexes can service queries that filter on any subset of the index keys.
- [x] If no indexes can be used then a collection scan will be necessary.
- [x] Query plans are removed from the plan cache on index creation, destruction, or server restart.

## Question 6

**Problem**

Which of the following statements is/are true?

**Answer**

- [x] You can use the --wiredTigerDirectoryForIndexes option to place your indexes on a different disk than your data.
- [x] The ideal ratio between nReturned and totalKeysExamined is 1.
- [ ] Indexes can only be traversed forward.
- [x] An index doesn't become multikey until a document is inserted that has an array value.
- [ ] Running performance tests from the mongo shell is an acceptable way to benchmark your database.

## Question 7

**Problem**

Given the following indexes:

1. { categories: 1, price: 1 }
2. { in_stock: 1, price: 1, name: 1 }

The following documents:

1. { price: 2.99, name: "Soap", in_stock: true, categories: ['Beauty', 'Personal Care'] }
2. { price: 7.99, name: "Knife", in_stock: false, categories: ['Outdoors'] }

And the following queries:

1. db.products.find({ in_stock: true, price: { $gt: 1, $lt: 5 } }).sort({ name: 1 })
2. db.products.find({ in_stock: true })
3. db.products.find({ categories: 'Beauty' }).sort({ price: 1 })

Which of the following is/are true?

**Answer**

- [ ] There would be a total of 4 index keys created across all of these documents and indexes.
- [ ] Index #2 properly uses the equality, sort, range rule for query #1.
- [x] Index #1 would provide a sort to query #3.
- [x] Index #2 can be used by both query #1 and #2.
