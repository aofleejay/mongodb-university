# Chapter 3: Patterns (Part 1)

## Quiz 1: Guide to Homework Validation

**Problem**

Please follow the steps outlined in this lecture and included in the lecture notes.

To run the validator for the example lab on Windows, run the following command:

```
validate_m320 example --file answer_schema.json
```

To run the validator for the example lab on MacOS and Linux, run the following command:

```
./validate_m320 example --file answer_schema.json
```

Then, paste the validation code from the example lab into the text box below and hit the submit button.

**Answer**

5d124f9bd971a774b97b5fc7

## Quiz 2: Handling Referential Integrity

**Problem**

Which of the following are valid concerns regarding duplication, staleness and referential integrity management in a MongoDB database and appropriate resolution techniques?

**Answer**

- [ ] Data duplication should not exist and can be avoided with multi-document transactions.
- [x] Data integrity issues can be minimized by using multi-document transactions.
- [x] Data staleness issues can be minimized with frequent batch updates.

## Quiz 3: Attribute Pattern

**Problem**

Which one of the following scenarios is best suited for the application of the Attribute Pattern?

**Answer**

- [ ] The documents are large.
- [x] Some fields share a number of characteristics, and we want to search across those fields.
- [ ] The working set does not fit in memory.
- [ ] The documents need strict validation.
- [ ] The system is accessing the disk too frequently.

## Lab: Apply the Attribute Pattern

**Problem**

**User Story**

The museum we work at has grown from a local attraction to one that is seen as having very popular items.

For this reason, other museums in the World have started exchanging pieces of art with our museum.

Our database was tracking if our pieces are on display and where they are in the museum.

To track the pieces we started exchanging with other museum, we added an array called events, in which we created an entry for each date a piece was loaned and the museum it was loaned to.

```
{
  "_id": ObjectId("5c5348f5be09bedd4f196f18"),
  "title": "Cookies in the sky",
  "artist": "Michelle Vinci",
  "date_acquisition": ISODate("2017-12-25T00:00:00.000Z"),
  "location": "Blue Room, 20A",
  "on_display": false,
  "in_house": false,
  "events": [{
    "moma": ISODate("2019-01-31T00:00:00.000Z"),
    "louvres": ISODate("2020-01-01T00:00:00.000Z")
  }]
}
```

The problem with this design is that we need to build a new index every time there is a new museum with which we start exchanging pieces. For example, when we started working with The Prado in Madrid, we needed to add this index:

```
{ "events.prado" : 1 }
```

**Task**

To address this issue, you've decided to change the schema to:

- use a single index on all event dates.
- transform the field that tracks the date when a piece was acquired, date_acquisition, so that it is also indexed with the values above.

To ensure the validator can verify your solution, use "k" and "v" as field names if needed.

To complete this lab:

- Modify the following schema to incorporate the above changes:

```
{
  "_id": "<objectId>",
  "title": "<string>",
  "artist": "<string>",
  "date_acquisition": "<date>",
  "location": "<string>",
  "on_display": "<bool>",
  "in_house": "<bool>",
  "events": [{
    "moma": "<date>",
    "louvres": "<date>"
  }]
}
```

**Solution**

```
{
  "_id": "<objectId>",
  "title": "<string>",
  "artist": "<string>",
  "location": "<string>",
  "on_display": "<bool>",
  "in_house": "<bool>",
  "events": [
    {
      "k": "<string>",
      "v": "<date>"
    }
  ]
}
```

**Answer**

02008affbe09bedd4f196f19

## Quiz 4: Extended Reference Pattern

**Problem**

Which one of the following scenarios is the best candidate to use the Extended Reference Pattern to avoid doing additional reads through joins/lookups?

**Answer**

- [x] An app needs to retrieve a product and information about its supplier.
- [ ] An app needs to retrieve a product and its ten most recent reviews.
- [ ] A product model needs to store a counter representing the number of times it was purchased.
- [ ] A product model needs to store references to images of the product that are kept in an external location outside the database.
- [ ] An order model needs to store the product ID, the price sold, and the quantity ordered for each product in an order.

## Quiz 5: Subset Pattern

**Problem**

Which one of the following scenarios is the best candidate for use of the Subset Pattern?

**Answer**

- [ ] The system is running out of RAM.
- [ ] The documents are too big.
- [ ] The system is accessing the disk too frequently
- [ ] The developers of the system have left and no one understands the application.
- [x] The working set does not fit in memory and it is difficult to scale the hardware.

## Lab: Apply the Subset Pattern

**Problem**

You are the lead developer for an online organic recycled clothing store. Consider the following user story:

**User Story**

Due to the growing number of environmentally-conscious consumers, our store's inventory has increased exponentially. We now also have an increasingly large pool of makers and suppliers.

We recently found that our shopping app is getting slower due to the fact that the frequently-used documents can no longer all fit in RAM. This is happening largely due to having all product reviews, questions, and specs stored in the same document, which grows in size as reviews and ratings keep coming in.

To resolve this issue, we want to reduce the amount of data immediately available to the user in the app and only load additional data when the user asks for it.

Currently a typical document in our data base looks like this:

```
{
  "_id": ObjectId("5c9be463f752ec6b191c3c7e"),
  "item_code": "AS45OPD",
  "name": "Recycled Kicks",
  "maker_brand": "Shoes From The Gutter",
  "price": 100.00,
  "description": "These amazing Kicks are made from recycled plastics and
  fabrics.They come in a variety of sizes and are completely unisex in design.
  If your feet don't like them within the first 30 days, we'll return your
  money no questions asked.
  ",
  "materials": [
    "recycled cotton",
    "recycled plastic",
    "recycled food waste",
  ],
  "country": "Russia",
  "image": "https:///www.shoesfromthegutter.com/kicks/AS45OPD.img",
  "available_sizes": {
      "mens": ["5", "6", "8", "8W", "10", "10W", "11", "11W", "12", "12W"],
      "womens": ["5", "6", "7", "8", "9", "10", "11", "12"]
  },
  "package_weight_kg": 2.00,
  "average_rating": 4.8,
  "reviews": [{
      "author": "i_love_kicks",
      "text": "best shoes ever! comfortable, awesome colors and design!",
      "rating": 5
    },
    {
      "author": "i_know_everything",
      "text": "These shoes are no good because I ordered the wrong size.",
      "rating": 1
    },
    "..."
  ],
  "questions": [{
      "author": "i_love_kicks",
      "text": "Do you guys make baby shoes?",
      "likes": 1223
    },
    {
      "author": "i_know_everything",
      "text": "Why do you make shoes out of garbage?",
      "likes": 0
    },
    "..."
  ],
  "stock_amount": 10000,
  "maker_address": {
    "building_number": 7,
    "street_name": "Turku",
    "city": "Saint-Petersburg",
    "country": "RU",
    "postal_code": 172091
  },
  "makers": ["Ilya Muromets", "Alyosha Popovich", "Ivan Grozniy", "Chelovek Molekula"],
}
```

**Task**

To address this user story, you must modify the following schema so that the working set can fit in RAM:

```
{
  "_id": "<objectId>",
  "item_code": "<string>",
  "name": "<string>",
  "maker_brand": "<string>",
  "price": "<decimal>",
  "description": "<string>",
  "materials": ["<string>"],
  "country": "<string>",
  "image": "<string>",
  "available_sizes": {
    "mens": ["<string>"],
    "womens": ["<string>"]
  },
  "package_weight_kg": "<decimal>",
  "average_rating": "<decimal>",
  "reviews": [{
    "author": "<string>",
    "text": "<string>",
    "rating": "<int>"
  }],
  "questions": [{
    "author": "<string>",
    "text": "<string>",
    "likes": "<int>"
  }],
  "stock_amount": "<int>",
  "maker_address": {
    "building_number": "<string>",
    "street_name": "<string>",
    "city": "<string>",
    "country": "<string>",
    "postal_code": "<string>"
  },
  "makers": ["<string>"]
}
```

**Solution**

```
{
  "_id": "<objectId>",
  "item_code": "<string>",
  "name": "<string>",
  "maker_brand": "<string>",
  "price": "<decimal>",
  "description": "<string>",
  "materials": ["<string>"],
  "country": "<string>",
  "image": "<string>",
  "available_sizes": {
    "mens": ["<string>"],
    "womens": ["<string>"]
  },
  "package_weight_kg": "<decimal>",
  "average_rating": "<decimal>",
  "top_five_reviews": [
    {
      "author": "<string>",
      "text": "<string>",
      "rating": "<int>"
    }
  ],
  "top_five_questions": [
    {
      "author": "<string>",
      "text": "<string>",
      "likes": "<int>"
    }
  ],
  "stock_amount": "<int>"
}
```

**Answer**

5c9c02e1f752ec6b191c3c7f
