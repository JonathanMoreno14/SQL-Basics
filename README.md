# SQL-Basics
SQL Basics learn by doing

SQL (pronounced "ess-que-el") is a standard language for accessing databases.

This is a list of basic SQL commands that will also include live examples using **MS SQL Server** and also instructions on how to setup your own MS SQL Server environment. 

*Examples coming soon*

[Microsoft SQL Server 2016 editions](https://www.microsoft.com/en-us/server-cloud/products/sql-server-editions/overview.aspx)

**SQL Statements – part 1**

SELECT

FROM

WHERE

ORDER BY

BETWEEN


##### SELECT

 * SELECT -The SELECT statement is used to select data from a database
 
 * FROM - The FROM clause is used to list the tables and any joins required for the SQL statement



```sql
SELECT * FROM table_name;
```

**Example:**

##### WHERE

* WHERE - The  WHERE clause is used to filter the results and apply conditions in a SELECT, INSERT, UPDATE, or DELETE statement 

```sql
SELECT column_name,column_name
FROM table_name
WHERE column_name operator value;
```

**Example:**

##### ORDER BY

* ORDER BY - The ORDER BY keyword sorts the records in ascending order by default. To sort the records in a descending order, you can use the DESC keyword.


```sql
SELECT column_name, column_name
FROM table_name
ORDER BY column_name ASC|DESC, column_name ASC|DESC;
```

**Example:**

##### BETWEEN

 * BETWEEN - The BETWEEN operator selects values within a range. The values can be numbers, text, or dates.

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```
**Example:**

***

**SQL Statements – part 2**

 INNER JOIN
 
 ON
 
 **INNER JOIN**
 

 * INNER JOIN - The INNER JOIN keyword selects all rows from both tables as long as there is a   match between the columns in both tables.
 * ON - Is part of the INNER JOINS 


```sql
SELECT column_name(s) FROM table1
INNER JOIN table2
ON table1.column_name=table2.column_name;
```

**Example:**

***

**SQL Statements – part 3**

GROUP BY

HAVING

##### GROUP BY

* GROUP BY - The GROUP BY statement is used in conjunction with the aggregate functions to group the result-set by one or more columns.


```sql
SELECT column_name, aggregate_function(column_name)
FROM table_name
WHERE column_name operator value
GROUP BY column_name;

/*
SQL aggregate functions return a single value, calculated from values in a column.

Useful aggregate functions:

AVG() - Returns the average value
COUNT() - Returns the number of rows
FIRST() - Returns the first value
LAST() - Returns the last value
MAX() - Returns the largest value
MIN() - Returns the smallest value
SUM() - Returns the sum
*/

```



**Example:**

##### HAVING

 * HAVING - The HAVING clause was added to SQL because the WHERE keyword could not be used with aggregate functions.


```sql
SELECT column_name, aggregate_function(column_name)
FROM table_name
WHERE column_name operator value
GROUP BY column_name
HAVING aggregate_function(column_name) operator value;
```

**Example:**

***

**SQL Statements – part 4**

DISTINCT

MAX

MIN

SUM

##### DISTINCT

* DISTINCT - The SELECT DISTINCT statement is used to return only distinct (different) values.

```sql
SELECT DISTINCT column_name,column_name
FROM table_name;
```

**Example:**

##### MAX

* MAX -  The MAX() function returns the largest value of the selected column.

```sql
SELECT MAX(column_name) FROM table_name;
```


**Example:**

##### MIN

* MIN - The MIN() function returns the smallest value of the selected column.

```sql
SELECT MIN(column_name) FROM table_name;
```
**Example:**


##### SUM

* SUM - The SUM() function returns the total sum of a numeric column.

```sql
SELECT SUM(column_name) FROM table_name;
```
**Example:**

***

**Creating a New Database - Part 5**

This is an example on how to create a new database using **MS SQL SERVER**

*Screencast will be coming soon*

**Steps:**

*Step 1:*

 * On **Object Explorer** click on **Databases** right click and select **New Database…**

*Step 2:*

* A window will pop up you will need to input/enter a new **Database name:** example *New_DB_Test* then press the **OK** button

Finally the new Database has been created

**Example:**


***

**SQL Statements – part 6**

CREATE TABLE 

INSERT INTO

DELETE  

UPDATE

SELECT INTO 

ALTER TABLE

##### CREATE TABLE

* CREATE TABLE  - The CREATE TABLE statement is used to create a table in a database.

```sql
CREATE TABLE table_name
(
column_name1 data_type(size),
column_name2 data_type(size),
column_name3 data_type(size),
);
```
**Example:**

*Screenshots coming soons*

**Creating a  table**

Right click on the Database you are wanting to create the new table for, example: *New_DB_Test*   then select **New Query**

Within the query dashboard Input/enter the table information then press **Execute**  the table  will then be created. 


```sql
CREATE TABLE Persons
(
PersonID int,
LastName varchar(255),
FirstName varchar(255),
Address varchar(255),
City varchar(255)
);

```

##### INSERT INTO

* INSERT INTO - The INSERT INTO statement is used to insert new records in a table.

```sql
INSERT INTO table_name (column1,column2,column3,...)
VALUES (value1,value2,value3,...);
```
**Example:**

This example is using the *Persons* table that was mentioned before

```sql
INSERT INTO Persons (PersonID, LastName, FirstName, Address, City)
VALUES('1', 'Smith', 'John', '123 Main St.', 'Fort Worth');
```
##### DELETE 

* DELETE - The DELETE statement is used to delete rows in a table.

```sql
DELETE FROM table_name
WHERE some_column=some_value;
```
**Example:**

Suppose we wanted to delete row 2 from the *Persons* table you would input the following

```sql
DELETE FROM Persons
WHERE PersonID=2;
```

##### UPDATE

* UPDATE - The UPDATE statement is used to update records in a table.

```sql
UPDATE table_name
SET column1=value1,column2=value2,...
WHERE some_column=some_value;
```
**Example:**

We will update row 2 **City** from *Fort Worth* to  *Dallas* using the **Persons** table


```sql
UPDATE Persons
SET City = 'Dallas'
WHERE City = 'Fort Worth'
```
>-If you are wanting to update the specific table columns you can do so without the *WHERE* Clause and those specified columns on the table will be updated.  

```sql
UPDATE table_name
SET column1=value1,column2=value2,...
```

##### SELECT INTO

* SELECT INTO - The SELECT INTO statement copies data from one table and inserts it into a new table.


```sql
/*
We can copy all columns into the new table:
*/
SELECT *
INTO newtable [IN externaldb]
FROM table1;
/*
Or we can copy only the columns we want into the new table:
*/
SELECT column_name(s)
INTO newtable [IN externaldb]
FROM table1;
/*
The new table will be created with the column-names and types as defined in the SELECT statement. 
You can apply new names using the AS clause.
*/
```

**Example:**

We will add data from *Persons* table into a new table; *Employees*

```sql
/*
Database:
       New_DB_Test
Tables:
       Persons
       Employees
*/
SELECT FirstName, LastName, PersonID 
INTO Employees
FROM Persons;
```

##### ALTER TABLE

* ALTER TABLE - The ALTER TABLE statement is used to add, delete, or modify columns in an existing table.

```sql
/*
To add a column in a table, use the following syntax:
*/
ALTER TABLE table_name
ADD column_name datatype
/*
To delete a column in a table, use the following syntax (some database systems don't allow deleting a column):
*/
ALTER TABLE table_name
DROP COLUMN column_name
```

**Example:**

*JobTitle* was added to the **Employees** table 

```sql
ALTER TABLE Employees
ADD JobTitle varchar(255)
```
If we want to add  job titles to the **Employees** table

```sql
UPDATE table_name
SET column1 = value1, column2 = value2...., columnN = valueN
WHERE [condition];

UPDATE Employees
SET JobTitle = 'CEO'
WHERE PersonID = 1;
```

```sql

```
***

**Microsoft SQL Server Management Studio**

Overview:
This is a screencast of the Microsoft SQL Server Management Studio

*Screencast will be coming soon*


***

**SQL Stored Procedure**



***

#### References

[W3 Schools - SQL Tutorial](http://www.w3schools.com/sql/)

[Tech on the Net](http://www.techonthenet.com/sql/index.php)

