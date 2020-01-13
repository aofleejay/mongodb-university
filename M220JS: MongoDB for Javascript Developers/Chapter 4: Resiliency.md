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

## Ticket: Timeouts
**Task**

For this ticket, you'll be required to modify the configuration of MongoClient to set a write timeout of 2500 milliseconds.

The MongoClient is initialized in the src/index.js file. A link to the URI connection settings is included here for your reference.

**Solution**

```
MongoClient.connect(
  process.env.MFLIX_DB_URI,
  { useNewUrlParser: true, poolSize: 50, wtimeout: 2500 },
)
```

**Answer**

5addf035498efdeb55e90b01
