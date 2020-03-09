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

## Lab: Many-to-Many Relationship

**Problem**

Given the following Collection Relationship Diagram (CRD), identify the relationships that represent Many-to-Many relationships.

We are asking you to identify not only direct Many-to-Many relationships, but also transitives ones. For example a user has a One-to-Many relationship with its reviews and a One-to-Many relationship with its credit cards, making a Many-to-Many relationship between the reviews and the credit cards.

![Lab many-to-many problem](/M320:%20Data%20Modeling/images/lab-many-to-many-problem.png)

**Answer**

- [x] users.credit_cards.number and items.reviews.body
- [x] items.sold_at and items.reviews.body
- [x] stores.address.street and items.description
- [ ] items.title and items.reviews.body
- [ ] users.shipping_address.street and items.reviews.body

## Quiz 4: One-to-One Relationship

**Problem**

Which of the following are valid ways to represent a one-to-one relationship with the document model in MongoDB?

**Answer**

- [x] Link to a single document in another collection.
- [x] Embed the fields as a sub-document in the document.
- [x] Embed the fields in the document.

## Lab: One-to-One Relationship

**Problem**

A legacy database has been ported to MongoDB, resulting in a set of collections that were mapped to their original tables. This port has been quickly identified as a poor solution.

We have been tasked with redesigning the employees collection to make better use of the document model to make the information clearer.

![Lab one-to-one problem](/M320:%20Data%20Modeling/images/lab-one-to-one-problem.png)

While we are restructuring the database, the Human Resources department would like us to move any confidential employee information to a different collection to make the information easier to protect.

Consider the following potential schema designs. Each of these designs represents an individual employee and the One-to-One relationship between all of their fields.

The ideal schema design should store:

- address information together as an embedded sub-document
- all of an employee's phone numbers together as an embedded sub-document
- all salary and bonus compensation information together as an embedded sub-document
- all confidential information in a separate collection

Once you've identified the ideal design, you can deepen your knowledge by trying to explain why each of the other options is not the preferred design choice.

**Answer**

- [x] ![Lab one-to-one answer](/M320:%20Data%20Modeling/images/lab-one-to-one-answer.png)

## Quiz 5: One-to-Zillions Relationship

**Problem**

Which of the following statements are true about one-to-zillions relationships?

**Answer**

- [x] The relationship representations that embed documents are not recommended.
- [x] We must take extra care when writing queries that retrieve data on the zillions side.
- [x] It is a special case of the one-to-many relationship.
