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
