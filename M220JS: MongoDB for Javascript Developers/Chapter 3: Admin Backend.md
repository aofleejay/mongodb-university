# Chapter 3: Admin Backend

## Ticket: User Report

**Task**

For this ticket, you'll be required to modify one method in commentsDAO.js, mostActiveCommenters. This method produces a report of the 20 most frequent commenters on the MFlix site.

Hint

This report is meant to be run from the backend by a manager that is very particular about the accuracy of data. Ensure that the read concern used in this read avoids any potential document rollback.

Remember to add the necessary changes in the pipeline to meet the requirements. More information can be found in the comments of the method.

**Solution**

```
const pipeline = [
  {
    $group: {
      _id: "$email",
      count: {
        $sum: 1,
      },
    },
  },
  {
    $sort: {
      count: -1,
    },
  },
  {
    $limit: 20,
  },
]
```

**Answer**

5accad3272455e5db79e4dad

## Ticket: Migration

**Task**

For this ticket, you'll be required to complete the command-line script located in the migrations directory of src called movie-last-updated-migration.js.

Things always change, and a requirement has come down that the lastupdated value in each document of the movies collection needs to be stored as an ISODate rather than a String.

Complete the script so it updates the format of lastupdated using a bulk write. You can find the exact Node.js syntax in the docs.

To perform the migration, run the script:

```
node movie-last-updated-migration.js
```

**Solution**

Query and projection

```
const predicate = { lastupdated: { $type: "string", $exists: true } }
const projection = { lastupdated: 1 }
```

Bulk write

```
mflix
  .collection("movies")
  .bulkWrite(moviesToMigrate)
```

**Answer**

5ad9f6a64fec134d116fb06f
