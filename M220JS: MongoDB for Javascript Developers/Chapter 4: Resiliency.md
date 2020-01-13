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

## Ticket: Handling Errors
**Task**

For this ticket, you'll be required to make the API more robust by handling exceptions. Specifically, what should happen if an incorrectly formatted _id is passed to the getMovieByID() method in moviesDAO.js?

In this case, an error will be thrown to getMovieByID() because of an invalid ID. However, the method does not need to return this error. Instead, if this error is thrown, the method should return null.

A try/catch block is already included for you in getMovieByID(). Use the variable e to figure out if the invalid ID error is being thrown, and then return null in this case.

**Solution**

```
static async getMovieByID(id) {
  try {
    const pipeline = [
      {
        $match: {
          _id: ObjectId(id),
        },
      },
      {
        $lookup: {
          from: "comments",
          let: {
            id: "$_id",
          },
          pipeline: [
            {
              $match: {
                $expr: {
                  $eq: ["$movie_id", "$$id"],
                },
              },
            },
            {
              $sort: {
                date: -1,
              },
            },
          ],
          as: "comments",
        },
      },
    ]
    return await movies.aggregate(pipeline).next()
  } catch (e) {
    console.error(`Something went wrong in getMovieByID: ${e}`)
    return null
  }
}
```

**Answer**

5ae9b76a703c7c603202ef22

## Ticket: Principle of Least Privilege
**Task**

For this ticket, you'll be required to add a new user on your Atlas cluster for the MFlix application to connect with.

The user should follow credentials:

username: mflixAppUser
password: mflixAppPwd
This user should have the readWrite role on the sample_mflix database. Use Add Default Privileges to assign the user this specific role.

After you have created this user, modify the SRV connection string in your configuration file so the application connects with the new username and password.

**Solution**

Go to MongoDB Atlas and select `Database Access` in `Security` tab. Choose `Add new user` then select `Default Privileges` and add role `readWrite` on `sample_mflix`.

**Answer**

5b61be29094dbae03bf30616
