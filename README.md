# My SQL Cheatsheet
Reminder for all the things about SQL

## Data types
### String Data Types

`CHAR(size)` or Character A FIXED length string (can contain letters, numbers, and special characters). The size parameter specifies the column length in characters - can be from 0 to 255. Default is 1. Used when a fixed amount of data. Example: Student ID Number Or ID Card Number

`VARCHAR(size)` or Variable Character  A VARIABLE length string (can contain letters, numbers, and special characters). The size parameter specifies the maximum column length in characters - can be from 0 to 65535. used when the amount of data is not fixed. Example: Password

`ENUM('value1','value2','..')` A string object that can have only one value, chosen from a list of possible values. If a value is inserted that is not in the list, a blank value will be inserted. The values are sorted in the order you enter them. Example: Male or Female, Yes Or No

### Numeric Data Types

`INT` Integers is a whole numbers with no decimal points Example: 5; 10; -100; 1000;

`DECIMAL (size, decimal)` An exact fixed-point number. The total number of digits is specified in size. The number of digits after the decimal point is specified in the decimal parameter. Example DECIMAL (2,1) = 36.5

### Other Data Types 
`DATE` Used to represent date in the format YYYY-MM-DD Example `'2018-07-25'` = 25 August 2018

`DATETIME`  date and time combination. Format: YYYY-MM-DD hh:mm:ss. Example: `'2018-07-25 13:25:00'`

`TIMESTAMP` Used for well-defined, exact point in time 

`BLOB` For BLOBs (Binary Large OBjects). Holds up to 65,535 bytes of data involves saving files in record Example: .xlsx .xml .doc .jpg etc.

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
    FOREIGN KEY (parent_column) REFERENCES parent_table(parent_column) ON DELETE CASCADE /* if this table has a connection with others table */
    UNIQUE KEY (column) /* if this table has a unique key */
);
```

### ALTER Statements

ALTER TABLE add a foreign key 
```SQL
ALTER TABLE table_name
ADD FOREIGN KEY (child_column) REFERENCES parent_table(parent_column) ON DELETE CASCADE
```
ALTER TABLE delete foreign key
```SQL
ALTER TABLE table_name
DROP FOREIGN KEY Constraint_name /* check costraint on ddl tab */
```
