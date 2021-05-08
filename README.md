# My SQL Cheatsheet
Reminder for all the things about SQL

## Data types
### String Data Types

`CHAR(size)` or Character A FIXED length string (can contain letters, numbers, and special characters). The size parameter specifies the column length in characters - can be from 0 to 255. Default is 1. Used when a fixed amount of data. 
</br>Example: Student ID Number Or ID Card Number

`VARCHAR(size)` or Variable Character  A VARIABLE length string (can contain letters, numbers, and special characters). The size parameter specifies the maximum column length in characters - can be from 0 to 65535. used when the amount of data is not fixed. 
</br>Example: Password

`ENUM('value1','value2','..')` A string object that can have only one value, chosen from a list of possible values. If a value is inserted that is not in the list, a blank value will be inserted. The values are sorted in the order you enter them. 
</br>Example: Male or Female, Yes Or No

### Numeric Data Types

`INT` Integers is a whole numbers with no decimal points Example: 5; 10; -100; 1000;

`DECIMAL (size, decimal)` An exact fixed-point number. The total number of digits is specified in size. The number of digits after the decimal point is specified in the decimal parameter. 
</br> Example DECIMAL (2,1) = 36.5

### Other Data Types 
`DATE` Used to represent date in the format YYYY-MM-DD 
</br> Example `'2018-07-25'` = 25 August 2018

`DATETIME`  date and time combination. Format: YYYY-MM-DD hh:mm:ss. 
</br> Example: `'2018-07-25 13:25:00'`

`TIMESTAMP` Used for well-defined, exact point in time 

`BLOB` For BLOBs (Binary Large OBjects). Holds up to 65,535 bytes of data involves saving files in record 
</br> Example: .xlsx .xml .doc .jpg etc.

## SQL COMMANDS

### CREATE Statements

Create Database

`CREATE DATABASE IF NOT EXISTS  database_name;`  
`CREATE SCHEMA IF NOT EXISTS  database_name;`  

Create Table
```SQL
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
    ...,
    PRIMARY KEY (column1), /* if this table has primary key */
    FOREIGN KEY (parent_column) REFERENCES parent_table(parent_column) ON DELETE CASCADE, /* if this table has a connection with others table */
    UNIQUE KEY (column) /* if this table has a unique key */
);
```

### ALTER Statements

ALTER TABLE add/drop a foreign key 
```SQL
ALTER TABLE table_name
ADD FOREIGN KEY (child_column) REFERENCES parent_table(parent_column) ON DELETE CASCADE

ALTER TABLE table_name
DROP FOREIGN KEY Constraint_name /* check costraint on ddl tab */
```

ALTER TABLE add/drop unique key
```SQL
ALTER TABLE table_name
ADD UNIQUE KEY (column_name);

ALTER TABLE table_name
DROP INDEX unique_key_name;
```


ALTER TABLE add column
```SQL
ALTER TABLE table_name
ADD COLUMN column_name data_types after/before column_that_already_exist;
```
ALTER TABLE CHANGE column name or add/remove default/not null values
```SQL
ALTER TABLE table_name
CHANGE COLUMN column_name column_name /* if you want to change column name second name should be differnet */ data_types DEFAULT "value";

ALTER TABLE table_name 
ALTER COLUMN column_name DROP DEFAULT;

ALTER TABLE table_name
CHANGE column coulmn_name column_name data_type not null; /*null to not null */

ALTER TABLE table_name
modify  coulmn_name data_type null; /*not null to null */
```

### SELECT Statement

`SELECT` 
collect some column/all from certain table
```SQL
SELECT column1,column2,column3,column3 FROM table_name;

SELECT * FROM table_name; /* * mean all */

SELECT DISTINCT FROM table_name; /* The SELECT DISTINCT statement is used to return only distinct (different) values. */
```

`SELECT WHERE` 
Let you collect some column/all for certain table with a condition 
</br> Example: Selecting data from buyers table with the name of = Anggita
```SQL
SELECT column1,column2,column3,column4 FROM table_name WHERE condition_1 = 'value';
```

`SELECT WHERE AND` 
Let you collect some column/all for certain table with combining two statement with different condition 
(more than 1 condition. MUST BE DIFFERENT CONDITION).
</br> Example: selecting data from buyers table with the name of = Anggita AND with the age of = 23
```SQL
SELECT column1,column2,column3,column4 FROM table_name where condition_1 = 'value1' AND condition_2 = 'value2';
```
`SELECT WHERE OR`
Let you collect some column/all for certain table with combining two statement with same condition but same different values 
(more than 1 condition. MUST BE SAME CONDITION).
</br> Example: selecting data from buyers table with the name of = anggita OR with the name of = bagas
```SQL
SELECT column1,column2,column3,column4, FROM table_name where condition_1 = 'value1' OR condition_1 = 'value2';
```

*OPERATOR PRECENDENCE NOTE*
AND > OR
</br> AND always comes first than OR
</br> if you want to use AND and OR in the same script you must use parentheses
</br> so the syntax should bee:
```SQL
SELECT * FROM table_name  WHERE condition_1 = 'value_1' AND (condition_2 = 'value2' OR conditon_2 = 'value3');
```

`SELECT WHERE IN / NOT IN`
Let you collect some data from collumn/all for certain table with combiing two state ment with same condition but different values (most efficient way than `OR`)
</br> Example 1: selecting data from buyers table with the same name of = IN Khoshi , Dyah 
</br> Example 2: selectiong data from buyers table not the same name of = NOT IN Bagas, Pratiwi (other than these two)
```SQL
SELECT * FROM table_name WHERE condition_1 IN ('value1','value'2,'value3');
```

`SELECT WHERE LIKE/NOT LIKE`
The LIKE operator is used in a WHERE clause to search for a specified pattern in a column.
`The percent sign (%) represents zero, one, or multiple characters`
` The underscore sign (_) represents one, single character`
</br> Example 1: selecting data from purchase date within = LIKE january 2020.
</br> Example 1: selecting data from purchase date beside = NOT LIKE january 2020.
```SQL
SELECT * FROM table_name WHERE condition_1 condition_2 LIKE (`value%');

SELECT * FROM table_name WHERE condition_1 condition_2 LIKE ('value_2');
```

`SELECT WHERE BETWEEN/NOT BETWEEN AND`
The BETWEEN operator selects values within a given range. The values can be numbers, text, or dates.
</br> Example 1: selecting data from price table = BETWEEN 100.000 AND 500.000
</br> Example 1: selecting data from price table = NOT BETWEEN 100.000 AND 500.00
``` SQL 
SELECT * FROM table_name WHERE condition_1 BETWEEN 'value1' AND 'value2';
SELECT * FROM table_name WHERE condition_1 NOT BETWEEN 'value1' AND 'value2';
```
`SELECT WHERE FROM ORDER BY ASC/DESC`
The ORDER BY keyword is used to sort the result-set in ascending or descending order.
The ORDER BY keyword sorts the records in ascending order by default. To sort the records in descending order, use the DESC keyword.
</br> Example 1: selecting data from purchase number ORDER BY DESC
```SQL
SELECT * FROM table_name ORDER BY column1,column2 ASC / DESC
```
