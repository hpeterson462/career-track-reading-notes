# Articles

## *Inside a Computer*

* Motherboard - main circuit board
  * thin plate that holds the CPU, memory, connectors for the hard drive and optical drives, expansion cards to control the video and audio, and connections to ports
* CPU/Processor
  * on the motherboard
  * brain of computer
  * carries out commands
  * two-inch ceramic square with a silicon chip located inside - fits into motherboard's CPU socket and covered by heat sink
  * speed is measured in megahertz (MHz)
* RAM (random access memory)
  * short-term memory
  * disappears when turned off
  * measured in megabytes (MB) or gigabytes (GB)
  * more RAM = more computer can do at one time
* Hard drive
  * where software, documents, and other files are stored
  *  long-term storage - stores when computer is off
  * faster hard drive = faster computer can start up and load programs
* Power supply unit
  * converts the power from the wall outlet to the type of power needed by the computer
* Expansion cards
  * Video card
    * what you see on the monitor
    * most computers have a GPU (graphics processing unit) built into the motherboard instead of having a separate video card
  * Sound card
      * what you hear in the speakers or headphones
      * most motherboards have integrated sound
  * Network card
    * allows computer to communicate over a network and access Internet
    * many motherboards have built-in network connections
  * Bluetooth card (or adapter)
    * wireless communication over short distances
    * commonly built into the motherboard


## *PostgreSQL INSERT*

* `INSERT` inserts a new row into a table
  * `INSERT INTO table_name(column1, column2, …)
VALUES (value1, value2, …);`
  * returns command tag `INSERT oid count`
* `OID` is an object identifier
  * internal primary key for system tables
  * `INSERT` statement returns `OID` with value 0
  * `count` is the number of rows that `INSERT` successfully inserted into table
* optional `RETURN` that returns info of inserted row
  * `*` returns entire inserted row (or use id to return only some info of row)
  * `INSERT INTO table_name(column1, column2, …)
VALUES (value1, value2, …)
RETURNING *;`
* rename return value using `AS`
  * `RETURNING output_expression AS output_name;`
* to escape single quote use additional single quote
  * `INSERT INTO links (url, name)
VALUES('http://www.oreilly.com','O''Reilly Media');`
* `DATE` to insert date value into column
  * `'YYYY-MM-DD'` format
  * `INSERT INTO links (url, name, last_update)
VALUES('https://www.google.com','Google','2013-06-01');`
* `RETURNING` after `INSERT` statement will return last insert id
  * `INSERT INTO links (url, name)
VALUES('http://www.postgresql.org','PostgreSQL') 
RETURNING id;`


## *PostgreSQL SELECT*

* `SELECT` retrieves data from table
  * Select distinct rows using `DISTINCT` operator
  * Sort rows using `ORDER BY` clause
  * Filter rows using `WHERE` clause
  * Select a subset of rows from a table using `LIMIT` or `FETCH` clause
  * Group rows into groups using `GROUP BY` clause
  * Filter groups using `HAVING` clause
  * Join with other tables using joins such as `INNER JOIN, LEFT JOIN, FULL OUTER JOIN, CROSS JOIN` clauses
  * Perform set operations using `UNION, INTERSECT`, and `EXCEPT`
* `SELECT` data from single table
  * `SELECT
   select_list
FROM
   table_name;`
  * to specify list of columns, use `,` between two columns to separate
  * `FROM` clause is optional
* `;` used to separate two SQL statements
* Retrieving unnecessary data from the database increases the traffic between the database server and application server
  * only use `*` when necessary
* `SELECT` statement expressions
  * `SELECT 
   first_name || ' ' || last_name,
   email
FROM 
   customer;`
   * to select all first, last names and emails
  * `SELECT 5 * 3;`
    * output is `15` in one column


## *PostgreSQL UPDATE*


* `UPDATE` statement allows you to modify data in a table
  * `UPDATE table_name
SET column1 = value1,
    column2 = value2,
    ...
WHERE condition;`
* `WHERE` is optional
  * if not used, `UPDATE` will update all rows in table
* When the `UPDATE` statement is executed successfully, it returns `count`
  * `count` - number of rows updated including rows whose values did not change
* optional `RETURNING` that returns updated rows
  * `UPDATE table_name
SET column1 = value1,
    column2 = value2,
    ...
WHERE condition
RETURNING * | output_expression AS output_name;`
* updating 1 row with id of 3
  * `UPDATE courses
SET published_date = '2020-08-01' 
WHERE course_id = 3;`
* updating a row and returning the updated row
  * `UPDATE courses
SET published_date = '2020-07-01'
WHERE course_id = 2
RETURNING *;`


## *PostgreSQL DELETE*

* delete one or more rows from table
  * `DELETE FROM table_name
WHERE condition;`
* `WHERE` is optional 
* `DELETE` statement returns the number of rows deleted
  * returns zero if the `DELETE` statement did not delete any row
* delete all rows 
  * `DELETE FROM table_name
WHERE condition
RETURNING (select_list | *)`
* delete one row with the id 8 from the `links` table
  * `DELETE FROM links
WHERE id = 8;`
  * returns 1 to indicate one row has been deleted
    * `DELETE 1`
* deletes two rows from the links table and return the values in the id column of deleted rows
  * `DELETE FROM links
WHERE id IN (6,5)
RETURNING *;`