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
