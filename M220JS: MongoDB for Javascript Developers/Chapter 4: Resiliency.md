# Chapter 4: Resiliency
## Ticket: Connection Pooling
**Task**

For this ticket, you'll be required to modify the configuration of the MongoClient to set the maximum size of the connection pool to 50 connections.

The MongoClient is initialized in the src/index.js file. A link to the URI connection settings is included here for your reference.

**Solution**

```
MongoClient.connect(
  process.env.MFLIX_DB_URI,
  { useNewUrlParser: true, poolSize: 50 },
)
```

**Answer**

5ad4f4f58d4b377bcf55d742
