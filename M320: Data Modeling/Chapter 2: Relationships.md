# Chapter 2: Relationships

## Quiz 1: Relationship Types and Cardinality

**Problem**

Why did we introduce the one-to-zillions relationship in our modeling notation?

**Answer**

- [x] To address the fact that the concept of relationship linked to a huge number of entities is missing in normal crow's foot notation.
- [ ] To address the fact that a crow's foot has 5 fingers, not 3.
- [x] To highlight the fact that huge cardinalities may impact design choices.

## Quiz 2: One-to-Many Relationship

**Problem**

Consider a one-to-many relationship observed between a county and the cities in that county.

Which of the following are valid ways to represent this one-to-many relationship with the document model in MongoDB?

**Answer**

- [x] Embed the entities for the cities as an array of sub-documents in the corresponding county document.
- [ ] Embed all the fields for a city as a subdocument in the corresponding county document.
- [x] Have a collection for the counties and a collection for the cities with each city document having a field to reference the document of its county.

## Quiz 3: Many-to-Many Relationship

**Problem**

Consider a many-to-many relationship observed between movies and the actors starring in these movies, for a system that could provide detailed information about either a movie or an actor.

![Quiz 3 Problem](/M320:%20Data%20Modeling/images/quiz3-problem.png)

Which of the following are true about modeling this many-to-many relationship with the document model in MongoDB?

**Answer**

- [ ] When using one collection for movies and one collection for actors, all movie documents must have an array of references to the actors in that movie, and all actor documents must have an array of references to the movies they appear in.
- [x] Embedding actors in movies still requires a separate collection to store all actors.
- [x] Embedding actors in movies creates duplication of actor information.
