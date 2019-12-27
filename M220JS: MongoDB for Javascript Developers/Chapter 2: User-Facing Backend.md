# Chapter 2: User-Facing Backend
## Ticket: Paging
**Task**

Modify the method getMovies in moviesDAO.js to allow the application to display new pages of movies.

**Solution**

```
const displayCursor = cursor.skip(page * moviesPerPage).limit(moviesPerPage)
```

**Answer**

5a9824d057adff467fb1f526

## Ticket: Faceted Search
**Task**

For this Ticket, you'll be required to implement one method in moviesDAO.js, facetedSearch, so the MFlix application can perform faceted searches.

**Solution**
```
const queryPipeline = [
  matchStage,
  sortStage,
  skipStage,
  limitStage,
  facetStage,
]
```

**Answer**

5aa7d3948adcc3fb770f06fb

## Ticket: User Management
**Task**

For this Ticket, you'll be required to implement all the methods in usersDAO.js that are called by the API endpoints in users.controller.js. Specifically, you'll implement:

- getUser
- addUser
- loginUser
- logoutUser
- getUserSession

Registering a new user will insert a document into the users collection, and logging in a user will insert a document into the sessions collection.

There is a unique index on the user_id field in sessions, so we can efficiently query on this field.

**Solution**

getUser
```
users.findOne({ email })
```

addUser
```
const { name, password, email } = userInfo
users.insertOne({ name, password, email })
```

loginUser
```
sessions.updateOne(
  { user_id: email },
  { $set: { jwt } },
  { upsert: true },
)
```

logoutUser
```
sessions.deleteOne({ user_id: email })
```

getUserSession
```
sessions.findOne({ user_id: email })
```

**Answer**

5a8d8ee2f9588ca2701894be

## Ticket: Durable Writes
**Task**

For this ticket, you'll be required to increase the durability of the addUser method in UsersDAO.js from the default write concern of w: 1.

When a new user registers for MFlix, their information must be added to the database before they can do anything else on the site. For this reason, we want to make sure that the data written by the addUser method will not be rolled back in the case of a network or server error.

We can decrease the chances of a rollback by increasing the write durability of the addUser method. To use a non-default write concern with the insert() method, pass a new Object to the method specifying the level of write concern. You can read more about this in the Node.js docs.

**Solution**
```
users.insertOne({ name, password, email }, { w: "majority" })
```

**Answer**

w: "majority", w: 2

## Ticket: User Preferences
**Task**

For this Ticket, you'll be required to implement one method in usersDAO.js, updatePreferences. This method allows updates to be made to the "preferences" field in the users collection.

**Solution**
```
users.updateOne(
  { email },
  { $set: { preferences } },
)
```

**Answer**

5aabe31503ac76bc4f73e267
