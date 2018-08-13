# SQL Homework

The local cinema are having a Marvel Movie Marathon! They have asked you to help maintain their database of movies with times and attendees.

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

Use the supplied data as the source of data to answer the questions. Copy the SQL command you have used to get the answer, and paste it below the question, along with the result they gave.

## Questions

1.  Return ALL the data in the 'movies' table.

```SELECT * FROM movies;

id |                title                | year | show_time
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 15:15
  2 | The Incredible Hulk                 | 2008 | 22:05
  3 | Iron Man 2                          | 2010 | 18:05
  4 | Thor                                | 2011 | 13:00
  5 | Captain America: The First Avenger  | 2011 | 22:15
  6 | Avengers Assemble                   | 2012 | 23:25
  7 | Iron Man 3                          | 2013 | 12:05
  8 | Thor: The Dark World                | 2013 | 13:25
  9 | Batman Begins                       | 2005 | 23:55
 10 | Captain America: The Winter Soldier | 2014 | 19:40
 11 | Guardians of the Galaxy             | 2014 | 18:55
 12 | Avengers: Age of Ultron             | 2015 | 21:10
 13 | Ant-Man                             | 2015 | 15:20
 14 | Captain America: Civil War          | 2016 | 22:45
 15 | Doctor Strange                      | 2016 | 22:00
 16 | Guardians of the Galaxy 2           | 2017 | 15:30
(16 rows)

2.  Return ONLY the name column from the 'people' table

SELECT name FROM  people;

name        
-------------------
John Allan
Colin Bell
Graeme Broose
Stuart Bryce
Christopher Burn
David Clarkson
Samuel DaBell
Crawford Davidson
Natasha Ford
Dale Johnston
Harvey Wheaton
Kieran Marshall
Stephen Ng
Michael Robertson
Jia Wong
Craig Morton
(16 rows)

3.  Oops! Someone at CodeClan spelled Graham's name wrong! Change it to reflect the proper spelling ('Graeme Broose' should be 'Graham Bruce').

UPDATE people
  SET name = 'Graham Bruce',
	WHERE id = 3;

  name        
-------------------
John Allan
Colin Bell
Stuart Bryce
Christopher Burn
David Clarkson
Samuel DaBell
Crawford Davidson
Natasha Ford
Dale Johnston
Harvey Wheaton
Kieran Marshall
Stephen Ng
Michael Robertson
Jia Wong
Craig Morton
Graham Bruce
(16 rows)

4. Insert your name into the 'people' table.

```INSERT INTO people (name)
    VALUES ('Alison Babington Smith');

  name          
------------------------
John Allan
Colin Bell
Graeme Broose
Stuart Bryce
Christopher Burn
David Clarkson
Samuel DaBell
Crawford Davidson
Natasha Ford
Dale Johnston
Harvey Wheaton
Kieran Marshall
Stephen Ng
Michael Robertson
Jia Wong
Craig Morton
Alison Babington Smith
(17 rows)

5.  Return ONLY your name from the 'people' table.

```SELECT name FROM people
  WHERE id = 17;

```          name          
------------------------
 Alison Babington Smith
(1 row)


6.  The cinema is showing 'Batman Begins', but Batman is DC, not Marvel! Delete the entry from the 'movies' table.

```DELETE FROM movies
     WHERE title = 'Batman Begins';

  1 | Iron Man                            | 2008 | 15:15
    2 | The Incredible Hulk                 | 2008 | 22:05
    3 | Iron Man 2                          | 2010 | 18:05
    4 | Thor                                | 2011 | 13:00
    5 | Captain America: The First Avenger  | 2011 | 22:15
    6 | Avengers Assemble                   | 2012 | 23:25
    7 | Iron Man 3                          | 2013 | 12:05
    8 | Thor: The Dark World                | 2013 | 13:25
   10 | Captain America: The Winter Soldier | 2014 | 19:40
   11 | Guardians of the Galaxy             | 2014 | 18:55
   12 | Avengers: Age of Ultron             | 2015 | 21:10
   13 | Ant-Man                             | 2015 | 15:20
   14 | Captain America: Civil War          | 2016 | 22:45
   15 | Doctor Strange                      | 2016 | 22:00
   16 | Guardians of the Galaxy 2           | 2017 | 15:30
  (15 rows)

7.  Create a new entry in the 'people' table with the name of one of the instructors.
```INSERT INTO people(name)
     VALUES('Keith Douglas');


8.  Craig has decided to hijack our movie evening, Remove him from the table of people.

```DELETE from people
     WHERE name = 'Craig Morton';

     id |       name        
    ----+-------------------
      1 | John Allan
      2 | Colin Bell
      3 | Graeme Broose
      4 | Stuart Bryce
      5 | Christopher Burn
      6 | David Clarkson
      7 | Samuel DaBell
      8 | Crawford Davidson
      9 | Natasha Ford
     10 | Dale Johnston
     11 | Harvey Wheaton
     12 | Kieran Marshall
     13 | Stephen Ng
     14 | Michael Robertson
     15 | Jia Wong
     17 | Keith Douglas
    (16 rows)

9.  The cinema has just heard that they will be holding an exclusive midnight showing of 'Avengers: Infinity War'!! Create a new entry in the 'movies' table to reflect this.

INSERT INTO movies (title, year, show_time)
  VALUES ('Avengers: Infinity War', 2016, 00.00);

id |                title                | year | show_time
----+-------------------------------------+------+-----------
 1 | Iron Man                            | 2008 | 15:15
 2 | The Incredible Hulk                 | 2008 | 22:05
 3 | Iron Man 2                          | 2010 | 18:05
 4 | Thor                                | 2011 | 13:00
 5 | Captain America: The First Avenger  | 2011 | 22:15
 6 | Avengers Assemble                   | 2012 | 23:25
 7 | Iron Man 3                          | 2013 | 12:05
 8 | Thor: The Dark World                | 2013 | 13:25
 9 | Batman Begins                       | 2005 | 23:55
10 | Captain America: The Winter Soldier | 2014 | 19:40
11 | Guardians of the Galaxy             | 2014 | 18:55
12 | Avengers: Age of Ultron             | 2015 | 21:10
13 | Ant-Man                             | 2015 | 15:20
14 | Captain America: Civil War          | 2016 | 22:45
15 | Doctor Strange                      | 2016 | 22:00
16 | Guardians of the Galaxy 2           | 2017 | 15:30
17 | Avengers: Infinity War              | 2016 | 0.00
(17 rows)



10.  The cinema would also like to make the Guardians movies a back to back feature. Find out the show time of "Guardians of the Galaxy" and set the show time of "Guardians of the Galaxy 2" to start two hours later.

```UPDATE movies
    SET show_time = 20.55
    WHERE id = 16;

    id |                title                | year | show_time
----+-------------------------------------+------+-----------
 1 | Iron Man                            | 2008 | 15:15
 2 | The Incredible Hulk                 | 2008 | 22:05
 3 | Iron Man 2                          | 2010 | 18:05
 4 | Thor                                | 2011 | 13:00
 5 | Captain America: The First Avenger  | 2011 | 22:15
 6 | Avengers Assemble                   | 2012 | 23:25
 7 | Iron Man 3                          | 2013 | 12:05
 8 | Thor: The Dark World                | 2013 | 13:25
 9 | Batman Begins                       | 2005 | 23:55
10 | Captain America: The Winter Soldier | 2014 | 19:40
11 | Guardians of the Galaxy             | 2014 | 18:55
12 | Avengers: Age of Ultron             | 2015 | 21:10
13 | Ant-Man                             | 2015 | 15:20
14 | Captain America: Civil War          | 2016 | 22:45
15 | Doctor Strange                      | 2016 | 22:00
17 | Avengers: Infinity War              | 2016 | 0.00
16 | Guardians of the Galaxy 2           | 2017 | 20.55
(17 rows)


## Extension

1.  Research how to delete multiple entries from your table in a single command.

```DELETE FROM movies
     WHEN id IN (2, 6, 9, 12);
