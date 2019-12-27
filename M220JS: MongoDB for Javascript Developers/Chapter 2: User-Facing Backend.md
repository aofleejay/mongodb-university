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
