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
