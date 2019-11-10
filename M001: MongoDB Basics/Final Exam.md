# Final Exam
## Final Exam: Question 1
**Question**

Connect to our class Atlas cluster from Compass and view the citibike.trips collection.

Use the schema view and any filters you feel are necessary to determine the range of values for the usertype field. Which of the following are values found in this collection for the field usertype?

**Answer**

"Subscriber" and "Customer".

## Final Exam: Question 2
**Question**

Connect to our class Atlas cluster from Compass and view the 100YWeatherSmall.data collection.

Using the Schema view, explore the wind field. The wind field has the value type of document. Which of the following best describes the schema of this embedded document?

**Answer**

Three fields -- two with the value type "document", one with the value type "string".

## Final Exam: Question 3
**Question**

Connect to our class Atlas cluster from Compass and view the 100YWeatherSmall.data collection.

What is the value type of the "wind.speed.rate" field?

**Answer**

double.

## Final Exam: Question 4
**Question**

Please connect to our class Atlas cluster and view the citibike database.

How many documents in the citibike.trips collection have the key tripduration set to null? Ignore any documents that do not contain the tripduration key.

**Answer**

2.

## Final Exam: Question 5
**Question**

Please connect to our class Atlas cluster and view the video.movies collection.

Which of the queries below would produce output documents that resemble the following. Check all that apply.

```
{ "title" : "P.S. I Love You" }
{ "title" : "Love Actually" }
{ "title" : "Shakespeare in Love" }
```

NOTE: We are not asking you to consider specifically which documents would be output from the queries below, but rather what fields the output documents would contain.

**Answer**

db.movies.find({}, {title: 1, _id: 0}).

## Final Exam: Question 6
**Question**

Please connect to our class Atlas cluster from the mongo shell or Compass and view the video.movies collection.

How many movies match the following criteria? - The cast includes either of the following actors: "Jack Nicholson", "John Huston". - The viewerRating is greater than 7. - The mpaaRating is "R".

**Answer**

8.
