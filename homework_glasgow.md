# SQL Homework


##NOTE TO SELF KELSIE. Where you have made changes to the SQL document, you can just insert these commands into terminal within the psql file to learn the commands. This will change the database too. Usually this would be done in the code document the way you have done.
The Glasgow Film Theatre are having a Marvel Movie Marathon! They have asked you to help maintain their database of movies with times and attendees.

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
##Terminal
SELECT * FROM movies;
2. Return ONLY the name column from the 'people' table
##Terminal
SELECT name FROM people;

Sarah Bartlett
 Kelsie Braidwood
 Liam Kavenns
 Daniel Childs
 Victor Chugbo
 Brian Cooke
 Patrick Cullen
 Roberto De Marco
 Ruaridh Dunbar
 Edward Fallon
 Hadsan Geele
 Paul Kelly
 John McCollum
 Andrew Lowrie
 Callum Mackenzie
 Chris Marshall
 Fraser McKay
 Lyle Mitchell
 Stuart O'Donnell
 Connor Rose
 Nikhil Sharma
 Scott Stevenson
(22 rows)

3. Oops! Someone at CodeClan spelled Liam's name wrong! Change it to reflect the proper spelling ('Liam Kavenns' should be 'Liam Cavens').
##SQL file
UPDATE people SET name = 'Liam Cavens' WHERE name = 'Liam Kavenns';
##Terminal
SELECT name FROM people WHERE name = 'Liam Cavens';
    name     
-------------
 Liam Cavens
(1 row)

4. Return ONLY your name from the 'people' table.
##Terminal
marvel=# SELECT name FROM people WHERE name = 'Kelsie Braidwood';
       name       
------------------
 Kelsie Braidwood
(1 row)

5. The cinema is showing 'Batman Begins', but Batman is DC, not Marvel! Delete the entry from the 'movies' table.
##SQL File ##attendances first
DELETE FROM attendances WHERE movie_id = 9;
DELETE FROM movies WHERE title = 'Batman Begins';
##Terminal
marvel=# SELECT title FROM movies;
                title                
-------------------------------------
 Iron Man
 The Incredible Hulk
 Iron Man 2
 Thor
 Captain America: The First Avenger
 Avengers Assemble
 Iron Man 3
 Thor: The Dark World
 Captain America: The Winter Soldier
 Guardians of the Galaxy
 Avengers: Age of Ultron
 Ant-Man
 Captain America: Civil War
 Doctor Strange
 Guardians of the Galaxy 2
(15 rows)

6. Create a new entry in the 'people' table with the name of one of the instructors.
##SQL file
INSERT INTO people (name) VALUES ('Ally');
##Terminal
marvel=# SELECT name FROM people;
       name       
------------------
 Sarah Bartlett
 Kelsie Braidwood
 Daniel Childs
 Victor Chugbo
 Brian Cooke
 Patrick Cullen
 Roberto De Marco
 Ruaridh Dunbar
 Edward Fallon
 Hadsan Geele
 Paul Kelly
 John McCollum
 Andrew Lowrie
 Callum Mackenzie
 Chris Marshall
 Fraser McKay
 Lyle Mitchell
 Stuart O'Donnell
 Connor Rose
 Nikhil Sharma
 Scott Stevenson
 Ally
 Liam Cavens
(23 rows)

7. John McCollum has decided to hijack our movie evening, Remove him from the table of people.
##SQL document
DELETE FROM attendances WHERE person_id = 13;
DELETE FROM people WHERE name = 'John McCollum';
##Terminal
marvel=# SELECT name FROM people;
       name       
------------------
 Sarah Bartlett
 Kelsie Braidwood
 Daniel Childs
 Victor Chugbo
 Brian Cooke
 Patrick Cullen
 Roberto De Marco
 Ruaridh Dunbar
 Edward Fallon
 Hadsan Geele
 Paul Kelly
 Andrew Lowrie
 Callum Mackenzie
 Chris Marshall
 Fraser McKay
 Lyle Mitchell
 Stuart O'Donnell
 Connor Rose
 Nikhil Sharma
 Scott Stevenson
 Ally
 Liam Cavens
(22 rows)

8. The cinema has just heard that they will be holding an exclusive midnight showing of 'Spider-man: Homecoming'!! Create a new entry in the 'movies' table to reflect this.
##SQL document
INSERT INTO movies (title, year, show_time) VALUES ('Spider-man: Homecoming', 2017, '16:40');
##Terminal
marvel=# SELECT * FROM movies;

 id |                title                | year | show_time
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 21:55
  2 | The Incredible Hulk                 | 2008 | 15:45
  3 | Iron Man 2                          | 2010 | 18:30
  4 | Thor                                | 2011 | 13:00
  5 | Captain America: The First Avenger  | 2011 | 23:45
  6 | Avengers Assemble                   | 2012 | 16:50
  7 | Iron Man 3                          | 2013 | 16:35
  8 | Thor: The Dark World                | 2013 | 21:55
 10 | Captain America: The Winter Soldier | 2014 | 15:30
 11 | Guardians of the Galaxy             | 2014 | 15:30
 12 | Avengers: Age of Ultron             | 2015 | 13:30
 13 | Ant-Man                             | 2015 | 19:25
 14 | Captain America: Civil War          | 2016 | 16:50
 15 | Doctor Strange                      | 2016 | 22:10
 16 | Guardians of the Galaxy 2           | 2017 | 16:30
(15 rows)

9. The cinema would also like to make the Guardian movies a back to back feature. Update the 'Guardians of the Galaxy' show time from 15:30 to 21:00, and the 'Guardians of the Galaxy 2' show time from '16:30' to '22:00'.

##SQL document
##update this to be...
UPDATE movies SET show_time = '21:00' WHERE title = 'Guardians of the Galaxy';
UPDATE movies SET show_time = '22:00' WHERE title = 'Guardians of the Galaxy 2';

##Terminal

marvel=# SELECT * FROM movies;
 id |                title                | year | show_time
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 21:55
  2 | The Incredible Hulk                 | 2008 | 15:45
  3 | Iron Man 2                          | 2010 | 18:30
  4 | Thor                                | 2011 | 13:00
  5 | Captain America: The First Avenger  | 2011 | 23:45
  6 | Avengers Assemble                   | 2012 | 16:50
  7 | Iron Man 3                          | 2013 | 16:35
  8 | Thor: The Dark World                | 2013 | 21:55
 10 | Captain America: The Winter Soldier | 2014 | 15:30
 12 | Avengers: Age of Ultron             | 2015 | 13:30
 13 | Ant-Man                             | 2015 | 19:25
 14 | Captain America: Civil War          | 2016 | 16:50
 15 | Doctor Strange                      | 2016 | 22:10
 17 | Spider-man: Homecoming              | 2017 | 16:40
 11 | Guardians of the Galaxy             | 2014 | 21:00
 16 | Guardians of the Galaxy 2           | 2017 | 22:00
(16 rows)

## Extension

1. Research how to delete multiple entries from your table in a single command.
Here we use the key word or, and need to declare the title = on both.
If we wanted to delete from two columns, we would use the key word AND.
So, if we only wanted to use the Guardians of the Galaxy it was showing at 12:00 we would use:
DELETE FROM movies WHERE title = 'Guardians of the Galaxy ' AND show_time = '12:00';
##SQL Document
DELETE FROM movies WHERE title = 'Iron Man 2' OR title = 'Avengers: Age of Ultron';
