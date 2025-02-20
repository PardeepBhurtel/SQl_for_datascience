
**SQL Scripts - Uses and Applications**
## SQL Scripts
# SQL scripts are a series of commands or a program that will be executed on an SQL server.

SQL scripts are useful for making complex database changes and can be used to create, modify, or delete database objects such as tables, views, stored procedures, and functions.

Applications of SQL Scripts
Here are some of the things that you can do with SQL scripts:

# Create tables
You can use SQL scripts to create new tables in your database. This is useful when you need to add new functionality to your application or when you want to store new types of data.

# Drop tables
SQL scripts often have commands to Drop tables from databases. This is especially important before Create table commands to make sure that a table with the same name doesnt exist in the database already.

# Insert data
SQL scripts can also be used to insert data into your tables. This is useful when you need to populate your database with test data or when you want to import data from an external source.

# Update data
You can use SQL scripts to update existing data in your tables. This is useful when you need to correct errors or update records based on changing business requirements.

# Delete data
SQL scripts can also be used to delete data from your tables. This is useful when you need to remove old or obsolete records from your database.

# Create views
Views are virtual tables that allow you to query data from multiple tables as if they were a single table. You can use SQL scripts to create views that simplify complex queries and make it easier to work with your data.

# Create stored procedures
Stored procedures are precompiled SQL statements that can be executed on demand. You can use SQL scripts to create stored procedures that encapsulate complex business logic and make it easier to manage your database.

# Create triggers
Triggers are special types of stored procedures that are automatically executed in response to certain events, such as an insert, update, or delete operation. You can use SQL scripts to create triggers that enforce business rules and maintain data integrity.

# Example: Creating Tables
Let us execute a script containing the CREATE TABLE commands for all the tables in a given dataset, rather than create each table manually by typing the DDL commands in the SQL editor.

Note the following points about these scripts.

SQL scripts are basically a set of SQL commands compiled in a single file.
Each command must be terminated with a delimiter or terminator. Most often, the default delimiter is a semicolon ;.
It is advisable to keep the extension of the file as .sql.
Upon importing this file in the phpMyAdmin interface, the commands in the file are run sequentially.

### Consider the following script

DROP TABLE IF EXISTS PATIENTS;
DROP TABLE IF EXISTS MEDICAL_HISTORY;
DROP TABLE IF EXISTS MEDICAL_PROCEDURES;
DROP TABLE IF EXISTS MEDICAL_DEPARTMENTS;
DROP TABLE IF EXISTS MEDICAL_LOCATIONS;
CREATE TABLE PATIENTS (
  PATIENT_ID CHAR(9) NOT NULL,
  FIRST_NAME VARCHAR(15) NOT NULL,
  LAST_NAME VARCHAR(15) NOT NULL,
  SSN CHAR(9),
  BIRTH_DATE DATE,
  SEX CHAR,
  ADDRESS VARCHAR(30),
  DEPT_ID CHAR(9) NOT NULL,
  PRIMARY KEY (PATIENT_ID)
);
CREATE TABLE MEDICAL_HISTORY (
  MEDICAL_HISTORY_ID CHAR(9) NOT NULL,
  PATIENT_ID CHAR(9) NOT NULL,
  DIAGNOSIS_DATE DATE,
  DIAGNOSIS_CODE VARCHAR(10),
  MEDICAL_CONDITION VARCHAR(100),
  DEPT_ID CHAR(9),
  PRIMARY KEY (MEDICAL_HISTORY_ID)
);
CREATE TABLE MEDICAL_PROCEDURES (
  PROCEDURE_ID CHAR(9) NOT NULL,
  PROCEDURE_NAME VARCHAR(30),
  PROCEDURE_DATE DATE,
  PATIENT_ID CHAR(9) NOT NULL,
  DEPT_ID CHAR(9),
  PRIMARY KEY (PROCEDURE_ID)
);
CREATE TABLE MEDICAL_DEPARTMENTS (
  DEPT_ID CHAR(9) NOT NULL,
  DEPT_NAME VARCHAR(15),
  MANAGER_ID CHAR(9),
  LOCATION_ID CHAR(9),
  PRIMARY KEY (DEPT_ID)
);
CREATE TABLE MEDICAL_LOCATIONS (
  LOCATION_ID CHAR(9) NOT NULL,
  DEPT_ID CHAR(9) NOT NULL,
  LOCATION_NAME VARCHAR(50),
  PRIMARY KEY (LOCATION_ID, DEPT_ID)
);

This script incorporates commands to first drop any tables with the mentioned names in the database. After that, the script contains commands to create 5 different tables. All these commands are executed sequentially on the interface.

# Reading: Examples to CREATE and DROP tables
Objective(s)
Create and Drop tables in the database.
Estimated time to complete: 5 minutes

# CREATE TABLE statement
In the previous video, we saw the general syntax to create a table:

CREATE TABLE TableName (
   COLUMN1 datatype,
   COLUMN2 datatype,
   COLUMN3 datatype, 
   ...
);

Consider the following examples:

Create a TEST table with two columns - ID of type integer and NAME of type varchar. For this, we use the following SQL statement.

CREATE TABLE TEST (
   ID int,
   NAME varchar(30)
);

Create a COUNTRY table with an integer ID column, a two-letter country code column, and a variable length country name column. For this, we may use the following SQL statement.

CREATE TABLE COUNTRY (
   ID int,
   CCODE char(2),
   Name varchar(60)
);

In the example above, make ID a primary key. Then, the statement will be modified as shown below.

CREATE TABLE COUNTRY (
   ID int NOT NULL,
   CCODE char(2),
   Name varchar(60)
   PRIMARY KEY (ID)
);

In the above example, the ID column has the NOT NULL constraint added after the datatype, meaning that it cannot contain a NULL or an empty value. This is added since the database does not allow Primary Keys to have NULL values.

# DROP TABLE
If the table you are trying to create already exists in the database, you will get an error indicating table XXX.YYY already exists. To circumvent this error, create a table with a different name or first DROP the existing table. It is common to issue a DROP before doing a CREATE in test and development scenarios.

### The syntax to drop a table is:

DROP TABLE TableName;
Copied!
For example, consider that you wish to drop the contents of the table COUNTRY if a table exists in the dataset with the same name. In such a case, the code for the last example becomes

DROP TABLE COUNTRY;
CREATE TABLE COUNTRY (
   ID int NOT NULL,
   CCODE char(2),
   Name varchar(60)
   PRIMARY KEY (ID)
);


## Reading: Examples to ALTER and TRUNCATE tables using MySQL

Objective(s)
At the end of this reading, you will be able to:

- Use the ALTER TABLE statement in the correct syntax.
- Use TRUNCATE statements in syntax.
- Execute examples of ALTER and TRUNCATE statements.
# ALTER TABLE
ALTER TABLE statements can be used to add or remove columns from a table, to modify the data type of columns, to add or remove keys, and to add or remove constraints. The syntax of the ALTER TABLE statement is:

### ADD COLUMN syntax

ALTER TABLE table_name
ADD column_name data_type;

A variation of the syntax for adding column is:

ALTER TABLE table_name
ADD COLUMN column_name data_type;

By default, all the entries are initially assigned the value NULL. You can then use UPDATE statements to add the necessary column values.

For example, to add a telephone_number column to the author table in the library database, the statement will be written as:

ALTER TABLE author 
ADD telephone_number BIGINT;




### Modify column data type

ALTER TABLE table_name
MODIFY column_name data_type;

Sometimes, the data presented may be in a different format than required. In such a case, we need to modify the data_type of the column. For example, using a numeric data type for telephone_number means you cannot include parentheses, plus signs, or dashes as part of the number. For such entries, the appropriate choice of data_type is CHAR.

To modify the data type, the statement will be written as:

ALTER TABLE author
MODIFY telephone_number CHAR(20);

The entries can then be updated using UPDATE statements. 


## TRUNCATE Table
TRUNCATE TABLE statements are used to delete all of the rows in a table. The syntax of the statement is:

TRUNCATE TABLE table_name;

So, to truncate the "author" table, the statement will be written as:

TRUNCATE TABLE author;


Note: The TRUNCATE statement will delete the rows and not the table.

 


# SQL Cheat Sheet: CREATE TABLE, ALTER, DROP, TRUNCATE

| Command                                                                                                                                                                                                    |     | Syntax                                                                                                                                                                  |     | Description                                                                                                                                                                       |     | Example                                                                                                            |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --- | ------------------------------------------------------------------------------------------------------------------ |
| CREATE TABLE                                                                                                                                                                                               |     | MySQL/DB2:  CREATE TABLE table_name (col1 datatype optional keyword, col2 datatype optional keyword,col3 datatype optional keyword,..., coln datatype optional keyword) |     | CREATE TABLE statement is to create the table. Each column in the table is specified with its name, data type and an optional keyword which could be PRIMARY KEY, NOT NULL, etc., |     | MySQL/DB2:  CREATE TABLE employee ( employee_id char(2) PRIMARY KEY, first_name varchar(30) NOT NULL, mobile int); |
| ALTER TABLE - ADD COLUMN                                                                                                                                                                                   |     | MySQL/DB2:                                                       Option 1. ALTER TABLE table_name ADD column_name_1 datatype....ADD COLUMN column_name_n datatype; Option 2. ALTER TABLE table_name ADD COLUMN column_name_1 datatype....ADD COLUMN column_name_n datatype; || ALTER TABLE statement is used to add the columns to a table.|	|MySQL/DB2 Option 1. ALTER TABLE employee ADD income bigint; Option 2. ALTER TABLE employee ADD COLUMN income bigint;|
| ALTER TABLE - ALTER COLUMN |	| MySQL:  ALTER TABLE table_name MODIFY COLUMN column_name_1 new_data_type;DB2: ALTER TABLE table_name ALTER COLUMN column_name_1 SET DATA TYPE datatype; || MySQL: ALTER TABLE MODIFY COLUMN  MODIFY COLUMN clause is used with the ALTER TABLE statement to modify the data type of columns. Db2: ALTER TABLE ALTER COLUMN  statement is used to modify the data type of columns.||MySQL: ALTER TABLE employee MODIFY COLUMN mobile SET DATA TYPE CHAR(20);DB2: ALTER TABLE employee ALTER COLUMN mobile SET DATA TYPE CHAR(20);|
| ALTER TABLE - DROP COLUMN|	|MySQL/DB2:  ALTER TABLE table_name DROP COLUMN column_name_1 ;|	|ALTER TABLE DROP COLUMN  statement is used to remove columns from a table.|	|MySQL/DB2: ALTER TABLE employee DROP COLUMN mobile ;|
| ALTER TABLE - RENAME COLUMN |	| MySQL:ALTER TABLE table_name CHANGE COLUMN current_column_name new_column_name datatype [optional keywords]; DB2: ALTER TABLE table_name RENAME COLUMN current_column_name TO new_column_name; || MySQL: ALTER TABLE CHANGE COLUMN  CHANGE COLUMN clause is used to rename the columns in a table. DB2: ALTER TABLE RENAME COLUMN  statement is used to rename the columns in a table. | |MySQL: ALTER TABLE employee CHANGE COLUMN first_name name VARCHAR(255); DB2: ALTER TABLE employee RENAME COLUMN first_name TO name;|
| TRUNCATE TABLE| 	|MySQL: TRUNCATE TABLE table_name; DB2: TRUNCATE TABLE table_name IMMEDIATE;|| MySQL: TRUNCATE TABLE statement is used to delete all of the rows in a table. Db2: The IMMEDIATE specifies to process the statement immediately and that it cannot be undone.||MySQL: TRUNCATE TABLE employee; DB2: TRUNCATE TABLE employee IMMEDIATE ;
|DROP TABLE|	|MySQL/DB2DROP TABLE table_name ;|	|Use the DROP TABLE statement to delete a table from a database. If you delete a table that contains data, by default the data will be deleted alongside the table.|	|MySQL/DB2: DROP TABLE employee ;|