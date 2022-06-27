# Database_Systems

- Database Management Systems (DBMS)
- Structured Query Language (SQL)

# we will be using a Database System if you 
- Enroll in a course
- Transfer money
- Shop on amazon
- Each application manages its own data in a custom format using ITS FILES

### The SQL Language

- Storeage media 
- Data layout 
- Files and indexes
- Operastors 
- Cost Estimation 
- Query Optimization

### How we process transaction?
Transactions are groups of commands either read or modify your data which are symmetrically related.
- Transaction Processing
- Concurrency Control 
- Crash Recovery

### How we can design a good Database?
- Schema Design 
- Detecting Redundancy 
- Schema Normalization

### Distributed Data Processing NoSQL and NewSQL
- Graph Data
- Spatial Data
- Data Streams

### SQL Intro
## The SQL language
- Used to issue commands to a database
- Used to query a database
- SQL : Structured Query Language
- The SQL standard is around 70's


### SQL Command Types

- DDL : Data Definition Language (Defines admissible database content / schema)
- DML : Data Manipulation Language (Manipulates database content)
- DCL : Data Control Language (assign data access rights)
- TCL : Transaction Control Language (gROUPS sql commands)

## Defing database schemas

- define relations with their schemas
- what columns and column types?
- define constarins restricting admissible content
 * Constraints on single relations
 * Constraints linking multiple relations

## Schema Definition in SQL

- CREATE TABLE< table >(< table-def >)
- < table > is the table name
- < table-def > is a list of column definitions
- Column definition is of form <col-name><col-type>

### What Constraints Do We Want?
-> Certain columns have certain datatypes

### Integrity Constraints
- constraints that limit admissible of tables 
- DBMS enforces integrity constraints 
- can be added to tables via " ALTER TABLE " command 
- Alternatively , can define when creating table

## Primary Key Constraints

- A primary key contraint refers to a "single table"
- It identifies a subset of columns as key columns
- Fixing values for key columns must identify row
- No two rows have same values in key columns

## Primary Key Syntax
- ALTER TABLE <table> ADD CONSTRAINT Primary Key (<key-cols>)
- <table> is the table name
- <key-cols> is comma-separated list of column names

## Foreign Key Constraints

- A foreign key constraint refers to a two table
- identifies set of foreign key columns in table 1
- maps foreign key columns nto primary key of table 2
- values in foriegn key columns must appear as primary
- maps each row in table 1 to a row from table 2

## Foreign Key Syntax
- ALTER TABLE <table-1> ADD CONSTRAINT Foreign Key (<fkey-columns>)
REFERENCES <table-2> (<pkey-columns>);
- <table-1> is the table with foreign key columns
- <fkey-columns> is comma-separated foreign key columns
- <table-2> is the table with primary key columns
- <pkey-columns> is comma-separated primary key columns

### Working with Data (DML)
- can Insert data into a table
- can delete data from a table
- can update data in a table
- can analyze data in a table

## Inserting Data
- Inserting one (fully specified) row into a table:
    * INSERT INTO <table> VALUES (<value-list>)
- Inserting one (partially specified) row into a table:
    * INSERT INTO <table> (<column-list>) VALUES (<value-list>)

## Inserting Data From Files
- Loading data from a file into a tabl:
	* COPY <table> FROM <path> DELIMITER <delimiter> NULL <null-string> CSV 

## Deleting Data
- Deleting rows from a table that satisfy condition:
	* DELETE FROM <table> WHERE <condition>
	* <condition> specifies Boolean predicate

## Updating Data
- Updating specific rows and columns to new value:
	* UPDATE <table> SET <column>=<value> WHERE <condition>
- Changes rows satisfying <condition> by writing <value> in <column>

### Simple SQL Queries 
- An SQL query describes a new relation to generate
- Simple SQL queries consist of 3 parts
	* SELECT : describes columns of relation to generate
	* FROM : describe source relations and how to match
	* WHERE : defines conditions result rows must satisfy

## Simple Query Format
- SELECT <columns> FROM <table1> JOIN <table2> ON (<join-pred>)… WHERE <where-pred>
- <columns> is a comma-separated list of columns
- <table1> and <table2> are database relations
- <join-pred> is condition defining matching tuples pairs
- <where-pred>  are additional conditions

## Diverse Select Clause
- Shortcuts for selecting multiple columns
	* *selects all columns
	* <table>.*selects all columns from <table>
- Can use arthmetic expressions in select clause
- Can assign new names for output columns

## Composite Predicates
- Logical conjunction via AND keyword
- Logical disjunction via OR keyword
- Negation via Not Keyword 

## Join Syntax Alternative
- Simply specify name of columns that appear in multiple tables
	* <table1> JOIN <table2> USING (<column>)
	* Abbreviates <table1> JOIN <table2> ON (<table1>.<column> = <table2>.<column>)
- “Natural joins” match values in columns with same name
	* <table1> NATURAL JOIN <table2>
	* Introduces equality conditions between columns of same name
- No join keyword: FROM <table1>,<table2> WHERE <join-condition>


## Aggregation queries

- can calculate aggregates over all the rows of the result relation.

- SQL Aggregates : COUNT, SUM, AVG, MIN, MAX

- COUNT: for counting rows in the result relation
- SUM: for summing up values in the result relation
- AVG: for calculating average of values in the result relation
- MIN: for finding minimum value in the result relation
- MAX: for finding maximum value in the result relation

## Aggregation by Group
- Common : want aggregates for multiple data subsets
- Use SQL GROUP-BY clause to define data subsets
	* GROUP-BY <column-list> - distinguish data subsets based on their values in specific columns
- GROUP BY: for grouping rows in the result relation

// SELECT
// FROM
// WHERE
// GROUP BY
// HAVING
// ORDER BY
// LIMIT
// OFFSET

## Grouping Details
-Grouping is applied after pairing data sources (FROM) and filtering rows (WHERE)
- Result contains one row per group 
	* Implies restrictions on SELECT clause!
	* Only expressions with unique value per group
	* This includes aggregates and grouping columns

## Predicates on Groups
- Condition WHERE clause applies to single rows (evaluated before grouping)
- Having clause specifies conditions on groups (evaluated after grouping)

