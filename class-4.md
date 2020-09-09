# Articles

## *Postgres SQL Joins*

* Inner Join
  * examines each row in both tables are compared
  * if values are equal, creates a new row that contains columns from both tables
* Left Join
  * examines data on left table
  * if values equal to right table, creates a new row that contains columns of both tables and adds this new row to the result set
  * if values  not equal, creates new row  that contains columns from both tables and adds it to the result set
* Right Join
  * examines data on right table
  * if values equal, creates new row that contains columns from both tables
  * if not equal, creates a new row that contains columns from both tables
* Full Outer Join
  * returns a result set that contains all rows from both left and right tables, with the matching rows from both sides


  ## *One-to-One (Data Model)*

  * In a relational database, a one-to-one relationship exists when one row in a table may be linked with only one row in another table and vice versa
  * One-to-one relationship is not a property of the data, but rather of the relationship itself
  * Mother - child relationship is not one-to-one because mother's can have more than one child (one-to-many)


## *One-to-Many (Data Model)*  

* A one-to-many relationship exists when one row in table A may be linked with many rows in table B, but one row in table B is linked to only one row in table A
* Opposite of one-to-many is many-to-one


## *Many-to-Many (Data Model)* 

* Usually implemented by means of an associative table (join table)
* Primary key for AB is formed from the two foreign keys
