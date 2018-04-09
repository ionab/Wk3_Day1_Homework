# SQL Homework

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
##SQL File 

6. Create a new entry in the 'people' table with the name of one of the instructors.

7. John McCollum has decided to hijack our movie evening, Remove him from the table of people.

8. The cinema has just heard that they will be holding an exclusive midnight showing of 'Spider-man: Homecoming'!! Create a new entry in the 'movies' table to reflect this.

9. The cinema would also like to make the Guardian movies a back to back feature. Update the 'Guardians of the Galaxy' show time from 15:30 to 21:00, and the 'Guardians of the Galaxy 2' show time from '16:30' to '22:00'.

## Extension

1. Research how to delete multiple entries from your table in a single command.
