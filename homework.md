# SQL Homework

The Dominion Cinema are having a Marvel Movie Marathon! They have asked you to help maintain their database of movies with times and attendees.

## To access the database:

First, create a database called 'marvel'
```
# terminal
createdb marvel
```

Next, run the provided SQL script to populate your database:
```
# terminal
psql -d marvel -f marvel.sql
```

Use the supplied data as the source of data to answer the questions.  Copy the SQL command you have used to get the answer, and paste it below the question, along with the result they gave.

## Questions

1. Return ALL the data in the 'movies' table.

SELECT * FROM movies;

 id |                title                | year | show_time
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 17:55
  2 | The Incredible Hulk                 | 2008 | 17:55
  3 | Iron Man 2                          | 2010 | 17:10
  4 | Thor                                | 2011 | 19:30
  5 | Captain America: The First Avenger  | 2011 | 18:50
  6 | Avengers Assemble                   | 2012 | 19:05
  7 | Iron Man 3                          | 2013 | 22:10
  8 | Thor: The Dark World                | 2013 | 23:30
  9 | Batman Begins                       | 2005 | 23:30
 10 | Captain America: The Winter Soldier | 2014 | 14:55
 11 | Guardians of the Galaxy             | 2014 | 19:05
 12 | Avengers: Age of Ultron             | 2015 | 14:35
 13 | Ant-Man                             | 2015 | 19:15
 14 | Captain America: Civil War          | 2016 | 12:35
 15 | Doctor Strange                      | 2016 | 21:30
(15 rows)

2. Return ONLY the name column from the 'people' table

SELECT name FROM people;

 Faisal Ali
 Samantha Campbell
 Jasmse Cox
 Upul Dissanayaka
 Martin Eguizabel
 Pedro Everett
 Filipe Granha
 Winston Ingram
 Fred
 Reece Jones
 Eugene Kim
 Steven MacDonald
 Fred
 Jamie Martin
 Ciaran McKenna
 Ross Murray
 Victoria Plows
 Finn Porter
 Tom Roddick
 Alan White
 Glen Young
(21 rows)


3. Oops! Someone at CodeClan spelled James' name wrong! Change it to reflect the proper spelling (change 'Jasmse Cox' to 'James Cox').

UPDATE people SET name = 'James Cox' WHERE name = 'Jasmse Cox';
[SELECT name FROM people; #to check name changd from 'Jasmse Cox' to 'James Cox']

UPDATE 1
       name
-------------------
 Faisal Ali
 Samantha Campbell
 Upul Dissanayaka
 Martin Eguizabel
 Pedro Everett
 Filipe Granha
 Winston Ingram
 Fred
 Reece Jones
 Eugene Kim
 Steven MacDonald
 Fred
 Jamie Martin
 Ciaran McKenna
 Ross Murray
 Victoria Plows
 Finn Porter
 Tom Roddick
 Alan White
 Glen Young
 James Cox
(21 rows)

4. Return ONLY your name from the 'people' table.

SELECT name FROM people WHERE name = 'Victoria Plows';

      name
----------------
 Victoria Plows
(1 row)

5. The cinema is showing 'Batman Begins', but Batman is DC, not Marvel! Delete the entry from the 'movies' table.

DELETE FROM movies WHERE title = 'Batman Begins';
[SELECT * FROM movies; # to check 'Batman Begins' was the one deleted]

DELETE 1
 id |                title                | year | show_time
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 17:55
  2 | The Incredible Hulk                 | 2008 | 17:55
  3 | Iron Man 2                          | 2010 | 17:10
  4 | Thor                                | 2011 | 19:30
  5 | Captain America: The First Avenger  | 2011 | 18:50
  6 | Avengers Assemble                   | 2012 | 19:05
  7 | Iron Man 3                          | 2013 | 22:10
  8 | Thor: The Dark World                | 2013 | 23:30
 10 | Captain America: The Winter Soldier | 2014 | 14:55
 11 | Guardians of the Galaxy             | 2014 | 19:05
 12 | Avengers: Age of Ultron             | 2015 | 14:35
 13 | Ant-Man                             | 2015 | 19:15
 14 | Captain America: Civil War          | 2016 | 12:35
 15 | Doctor Strange                      | 2016 | 21:30
 16 | Guardians of the Galaxy 2           | 2017 | 00:00
(15 rows)

6. Create a new entry in the 'people' table with the name of one of the instructors.

INSERT INTO people (name) VALUES ('Jarrod Bennie');

[SELECT name FROM people; #to check it was'Jarrod Bennie' added]

 Faisal Ali
 Samantha Campbell
 Jasmse Cox
 Upul Dissanayaka
 Martin Eguizabel
 Pedro Everett
 Filipe Granha
 Winston Ingram
 Fred
 Reece Jones
 Eugene Kim
 Steven MacDonald
 Fred
 Jamie Martin
 Ciaran McKenna
 Ross Murray
 Victoria Plows
 Finn Porter
 Tom Roddick
 Alan White
 Glen Young
 Jarrod Bennie
(22 rows)

7. Winston Ingram, has decided to hijack our movie evening, Remove him from the table of people.

DELETE FROM people WHERE name = 'Winston Ingram';
[SELECT name FROM people; run to check 'Winston Ingram' was deleted]

DELETE 1
       name
-------------------
 Faisal Ali
 Samantha Campbell
 Jasmse Cox
 Upul Dissanayaka
 Martin Eguizabel
 Pedro Everett
 Filipe Granha
 Fred
 Reece Jones
 Eugene Kim
 Steven MacDonald
 Fred
 Jamie Martin
 Ciaran McKenna
 Ross Murray
 Victoria Plows
 Finn Porter
 Tom Roddick
 Alan White
 Glen Young
 Jarrod Bennie
(21 rows)

8. Somehow the list of people includes two people named 'Fred'. Change these entries to the proper names ('Jack Jarvis', 'Victor McDade')

UPDATE people SET name = 'Jack Jarvis' WHERE id = 9;
UPDATE people SET name = 'Victor McDade' WHERE id = 13;
[SELECT name FROM people; #run to check names updated]

...
UPDATE 1
UPDATE 1
       name
-------------------
 Faisal Ali
 Samantha Campbell
 Jasmse Cox
 Upul Dissanayaka
 Martin Eguizabel
 Pedro Everett
 Filipe Granha
 Winston Ingram
 Reece Jones
 Eugene Kim
 Steven MacDonald
 Jamie Martin
 Ciaran McKenna
 Ross Murray
 Victoria Plows
 Finn Porter
 Tom Roddick
 Alan White
 Glen Young
 Jarrod Bennie
 Jack Jarvis
 Victor McDade
(22 rows)

9. The cinema has just heard that they will be holding an exclusive midnight showing of 'Guardians of the Galaxy 2'!! Create a new entry in the 'movies' table to reflect this.

INSERT INTO movies (title, year, show_time) VALUES ('Guardians of the Galaxy 2', 2017, '00:00');
[SELECT * FROM movies; #run to check movie inserted]


 id |                title                | year | show_time
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 17:55
  2 | The Incredible Hulk                 | 2008 | 17:55
  3 | Iron Man 2                          | 2010 | 17:10
  4 | Thor                                | 2011 | 19:30
  5 | Captain America: The First Avenger  | 2011 | 18:50
  6 | Avengers Assemble                   | 2012 | 19:05
  7 | Iron Man 3                          | 2013 | 22:10
  8 | Thor: The Dark World                | 2013 | 23:30
  9 | Batman Begins                       | 2005 | 23:30
 10 | Captain America: The Winter Soldier | 2014 | 14:55
 11 | Guardians of the Galaxy             | 2014 | 19:05
 12 | Avengers: Age of Ultron             | 2015 | 14:35
 13 | Ant-Man                             | 2015 | 19:15
 14 | Captain America: Civil War          | 2016 | 12:35
 15 | Doctor Strange                      | 2016 | 21:30
 16 | Guardians of the Galaxy 2           | 2017 | 00:00
(16 rows)

10. The cinema would also like to make the Guardian movies a back to back feature. Update the 'Guardians of the Galaxy' show time from 12:10 to 21:30

UPDATE movies SET show_time = '21:30' WHERE title = 'Guardians of the Galaxy';
[SELECT * FROM movies; #run to check movie show_time updated]

UPDATE 1
 id |                title                | year | show_time
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 17:55
  2 | The Incredible Hulk                 | 2008 | 17:55
  3 | Iron Man 2                          | 2010 | 17:10
  4 | Thor                                | 2011 | 19:30
  5 | Captain America: The First Avenger  | 2011 | 18:50
  6 | Avengers Assemble                   | 2012 | 19:05
  7 | Iron Man 3                          | 2013 | 22:10
  8 | Thor: The Dark World                | 2013 | 23:30
  9 | Batman Begins                       | 2005 | 23:30
 10 | Captain America: The Winter Soldier | 2014 | 14:55
 12 | Avengers: Age of Ultron             | 2015 | 14:35
 13 | Ant-Man                             | 2015 | 19:15
 14 | Captain America: Civil War          | 2016 | 12:35
 15 | Doctor Strange                      | 2016 | 21:30
 16 | Guardians of the Galaxy 2           | 2017 | 00:00
 11 | Guardians of the Galaxy             | 2014 | 21:30
(16 rows)

## Extension

1. Research how to delete multiple entries from your table in a single command.
DELETE FROM people WHERE id IN (2, 17, 18)
[# deletes persons from people table with those ids]