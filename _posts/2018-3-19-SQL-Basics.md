##SQL Basics (link)[http://www.sqlcourse.com/select.html]

* Structured Query Language
* Used to communicate with a database

**Table Basics**

* A database contains one or more tables
* Each table is uniquely identified by its name
* Each table has columns and rows:
	* Each column contains column name, data type, and other attributes for the column
	* Rows are records of the tables

**Selecting data**

* **select** statement
* used to query the db and retrieve data that match criteria that you specify at the **where** clause:
	* where "condition"
	* condition: =, >, <, >=, <=, <>, LIKE
		* LIKE: pattern matching operator
			* Allows you to select only rows that are "like" what you specify
			* %: wild card
			* Strings must be in single quotes
* Practice questions:
	* Display the first name and age for everyone that's in the table:
		```
		select first, age from empinfo;
		```
	* Display the first name, last name, and city for everyone that's not from Payson.
		```
		select first, last, city from empinfo
				where city <> 'Payson';
		```
	* Display all columns for everyone that is over 40 years old.
		```
		select * from empinfo
				where age > 40;
		```
	* Display the first and last names for everyone whose last name ends in an "ay".
		```
		select first, last from empinfo
				where last LIKE '%ay';
		```
	* Display all columns for everyone whose first name equals "Mary".
		```
		select * from empinfo
				where first = 'Mary';
		```
	* Display all columns for everyone whose first name contains "Mary".
		```
		select * from empinfo
				where first LIKE '%Mary%';
		```

**Creating Tables**

```
create table "tablename"
("column1" "data type",
 "column2" "data type",
 "column3" "data type");
```

**Inserting into a table**

* `insert`
* To insert/add a row into the table

```
insert into "tablename"
 (first_column,...last_column)
  values (first_value,...last_value);
```

**Updating Records**

* `update`
* To update/change records that match a specified criteria

```
Example:

update phone_book
  set area_code = 623
  where prefix = 979;
```

----
###DDL, DML, DCL and TCL

SQL commands can be divided into four subgroups:

* **DDL - Data Definition Language**
	* Deals with database chemas and descriptions of how the data should reside in the database
	* CREATE
	* ALTER
	* DROP
	* TRUNCATE
	* COMMENT
	* RENAME
* **DML - Data Manipulation Language**
	* Deals with data manipulation
	* SELECT
	* INSERT
	* UPDATE
	* DELETE
* **DCL - Data Control Language**
	* Mostly concerned with permissions, rights and other controls
	* GRANT
	* REVOKE
* **TCL - Transaction Control Language**
	* Deals with transactions within a database
	* COMMIT
	* ROLLBACK
	* SAVEPOINT
