# My SQL Cheatsheet
Reminder for all the things about SQL

## Data types
### String Data Types
`CHAR(size)` or Character A FIXED length string (can contain letters, numbers, and special characters). The size parameter specifies the column length in characters - can be from 0 to 255. Default is 1. Used when a fixed amount of data. Example: Student ID Number Or ID Card Number
`VARCHAR(size)` or Variable Character  A VARIABLE length string (can contain letters, numbers, and special characters). The size parameter specifies the maximum column length in characters - can be from 0 to 65535. used when the amount of data is not fixed. Example: Password
`ENUM('value1','value2','..')` A string object that can have only one value, chosen from a list of possible values. If a value is inserted that is not in the list, a blank value will be inserted. The values are sorted in the order you enter them. Example: Male or Female, Yes Or No

### Creating Database
`CREATE DATABASE IF NOT EXISTS  database_name;`  For creating database
`CREATE SCHEMA IF NOT EXISTS  database_name;`  For creating database
