# Chapter 1: Driver Setup
## Ticket: Connection
**Task**

MFlix will use MongoDB as a storage layer, so for this ticket you will build a connection from MFlix to Atlas.

Note: These instructions were included in the README.rst. If you already completed the .env file, you can skip to Testing and Running the Application.

1. First, make sure you've created a user on your Atlas cluster with read and write access to the mflix database.
The user name should be m220student and the password should be m220password.
Don't forget to whitelist your IP address!
2. Copy the connection string. Select that you'd like to connect with the Mongo shell, version 3.6 or later. This will give you the srv connection string.
3. Locate the file called dotenv_win or dotenv_unix (depending on your operating system) and replace the information within with your own srv connection string:

```
SECRET_KEY=super_secret_key_you_should_change
MFLIX_DB_URI=your_atlas_3.6_srv_connection_uri
MFLIX_NS=mflix
PORT=5000
```

Make sure not to wrap your Atlas SRV connection between quotes:

```
MFLIX_DB_URI=mongodb+srv://...
```

It's highly suggested you also change the SECRET_KEY to some very long, very random string. While this application is only meant for local use during this course, software has a strange habit of living a long time.

4. Rename dotenv_win or dotenv_unix to .env. You can do this by running the following command from the mflix-js directory:

```
mv dotenv_unix .env  # on Unix
ren dotenv_win .env  # on Windows
```

Note: Once you rename this file to .env, it will no longer be visible in Finder or File Explorer. However, it will be visible from Command Prompt or Terminal, so if you need to edit it again, you can open it from there:

```
vi .env       # on Unix
notepad .env  # on Windows
```

**Answer**

5a9026003a466d5ac6497a9d

## Ticket: Projection
**Task**

Implement the getMoviesByCountry method in src/dao/moviesDAO.js to search movies by country and use projection to return the title field. The _id field will be returned by default

**Answer**

5a94762f949291c47fa6474d

## Ticket: Text and Subfield Search
**Task**

For this ticket, you will need to modify the method genreSearchQuery in moviesDAO.js to allow the following movie search criteria:

- genres: finds movies that include any of the wanted genres.

The methods for text and cast searches are already implemented:

- textSearchQuery : performs a text search in the movies collection
- castSearchQuery: finds movies that include any of the specified cast

You just need to construct the query in genreSearchQuery that queries the movies collection by genre. This method should project all document fields.

A text index was created for you when you restored the collections with mongorestore, so these queries will be performant once they are implemented.

Hint

Check the implementation of similar formats of search criteria - the genres query should be similar.

**Answer**

5a96a6a29c453a40d04922cc
