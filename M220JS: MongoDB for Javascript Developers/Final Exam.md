# Final Exam

## Final: Question 1

**Question**

Assume a collection called elections that holds data about all United States Presidential Elections since 1789. All the documents in the elections collection look like this:

```
{
  year: 1828,
  winner: "Andrew Jackson",
  winner_running_mate: "John C. Calhoun",
  winner_party: "Democratic",
  winner_electoral_votes: 178,
  total_electoral_votes: 261
}
```

total_electoral_votes represents the total number of electoral votes that year, and winner_electoral_votes represents the number of electoral votes received by the winning candidates.

Which of the following queries will retrieve all the Republican winners with at least 160 electoral votes?

**Answer**

```
elections.find({ winner_party: "Republican", winner_electoral_votes: { "$gte": 160 } })
```

## Final: Question 2

**Question**

Consider a collection of phones called phones, used by a phone manufacturer to keep track of the phones currently in production.

Each document in phones looks like this:

```
{
  model: 5,
  date_issued : Date("2016-07-27T20:27:52.834Z"),
  software_version: 4.8,
  needs_to_update: false
}
```

There is an update required for phones with software_version earlier than 4.0. Anyone still using a version older than 4.0 will be asked to update.

The phone manufacturer wants to set the flag needs_to_update to true when the value of software_version is lower than 4.0. For example, a document like this one:

```
{
  model: 5,
  date_issued : Date("2014-03-04T14:23:43.123Z"),
  software_version: 3.7,
  needs_to_update: false
}
```

Should be updated to look like this:

```
{
  model: 5,
  date_issued : Date("2014-03-04T14:23:43.123Z"),
  software_version: 3.7,
  needs_to_update: true
}
```

Which of the following update statements will correctly perform this update?

**Answer**

```
phones.updateMany({ software_version: { "$lt": 4.0 } }, { "$set": { needs_to_update: true } })
```


## Final: Question 3

**Question**

Suppose an instance of MongoClient is created with the following settings:

```
import { MongoClient } from "mongodb"

const URI = "mongodb+srv://m220-user:m220-pass@m220-test.mongodb.net/test"

const testClient = await MongoClient.connect(
  URI,
  {
    authSource: "admin",
    connectTimeoutMS: 50,
    retryWrites: true,
    useNewUrlParser: true
  },
)

const clientOptions = testClient.s.options
```

The variable representing our client, testClient, will:

**Answer**

- [x] automatically retry writes that fail.
- [x] wait at most 50 milliseconds for timing out a connection.
- [ ] authenticate against the test database.
- [ ] allow a maximum of 50 connections in the connection pool.
- [x] use SSL when connecting to MongoDB.

## Final: Question 4

**Question**

Suppose a client application is sending writes to a replica set with 3 nodes:

Before returning an acknowledgement back to the client, the replica set waits.

When the write has been applied by the nodes marked in stripes, it returns an acknowledgement back to the client.

What Write Concern was used in this operation?

**Answer**

- [ ] w: 1
- [ ] w: available
- [x] w: majority
- [ ] w: 0

## Final: Question 5

**Question**

Given the following bulk write statement, to a collection called employees:

```
const baseballPlayers = [
  { insertOne: { '_id': 11, 'name': 'Edgar Martinez', 'salary': "8.5M" }},    // Insert #1
  { insertOne: { '_id': 3, 'name': 'Alex Rodriguez', 'salary': "18.3M" }},    // Insert #2
  { insertOne: { '_id': 24, 'name': 'Ken Griffey Jr.', 'salary': "12.4M" }},  // Insert #3
  { insertOne: { '_id': 11, 'name': 'David Bell', 'salary': "2.5M" }},        // Insert #4
  { insertOne: { '_id': 19, 'name': 'Jay Buhner', 'salary': "5.1M" }}         // Insert #5
]

const bulkWriteResponse = employees.bulkWrite(baseballPlayers)
```

Assume the employees collection is empty, and that there were no network errors in the execution of the bulk write.

Which of the insert operations in requests will succeed?

**Answer**

- [x] Insert #1
- [x] Insert #2
- [x] Insert #3
- [ ] Insert #4
- [ ] Insert #5
