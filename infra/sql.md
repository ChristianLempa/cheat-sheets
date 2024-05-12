# SQL Cheat-Sheet

## Data Definition Language (DDL)

| Command | Description |
| --- | --- |
| `CREATE DATABASE <db>` | Create a new database |
| `DROP DATABASE <db>` | Delete a database |
| `CREATE TABLE <table> (<column_1> <column_1_type>, <column_2> <column_2_type>)` | Create a new table |
| `DROP TABLE <table>` | Delete a table |
| `ALTER TABLE <table> ADD COLUMN <column> <column_type>` | Add a new column to a table |
| `ALTER TABLE <table> DROP COLUMN <column>` | Remove a column from a table |
| `ALTER TABLE <table> RENAME COLUMN <column> TO <new_column>` | Rename a column in a table |
| `ALTER TABLE <table> RENAME TO <new_column>` | Rename a table |
| `TRUNCATE TABLE <table>` | Remove all rows from a table |
| `CREATE INDEX INDEXNAME ON <table> (<column>)` | Create an index on a table |
| `DROP INDEX INDEXNAME` | Remove an index from a table |

## Data Manipulation Language (DML)

| Command | Description |
| --- | --- |
| `INSERT INTO <table> (<column_1>, <column_2>) VALUES (<value_1>, <value_2>)` | Insert a new row into a table |
| `SELECT * FROM <table>` | Retrieve all rows from a table |
| `UPDATE <table> SET <column_1> = <value_1> WHERE <column_2> = <value_2>` | Update rows in a table |
| `DELETE FROM <table> WHERE <column> = <value>` | Delete rows from a table |

## Data Query Language (DQL)

| Command | Description |
| --- | --- |
| `SELECT <column_1>, <column_2> FROM <table>` | Retrieve specific columns from a table |
| `SELECT * FROM <table> WHERE <column> = VALUE` | Retrieve rows that match a condition |
| `SELECT * FROM <table> ORDER BY <column>` | Retrieve rows sorted by a column |
| `SELECT * FROM <table> LIMIT N` | Retrieve the first N rows from a table |
| `SELECT * FROM <table> OFFSET N` | Retrieve rows starting from the Nth row |
| `SELECT * FROM <table> JOIN <table_2> ON <table_1>.<column_1> = <table_2>.<column_2>` | Retrieve rows from two tables that match a condition |
| `SELECT * FROM <table> UNION SELECT * FROM <table_2>` | Retrieve rows from two tables without duplicates |
| `SELECT * FROM <table> GROUP BY <column>` | Group rows that have the same value in a column |
| `SELECT * FROM <table> HAVING COUNT(<column>) > N` | Filter grouped rows that have more than N rows |
| `SELECT * FROM <table> WHERE <column> IN (<value_1>, <value_2>)` | Retrieve rows where a column value matches any value in a list |
| `SELECT * FROM <table> WHERE <column> BETWEEN <value_1> AND <value_2>` | Retrieve rows where a column value is within a range |
| `SELECT * FROM <table> WHERE <column> LIKE '<value>%'` | Retrieve rows where a column value matches a pattern |
| `SELECT * FROM <table> WHERE <column> IS NULL` | Retrieve rows where a column value is NULL |
| `SELECT * FROM <table> WHERE <column> IS NOT NULL` | Retrieve rows where a column value is not NULL |

## Data Control Language (DCL)

| Command | Description |
| --- | --- |
| `GRANT PERMISSIONS ON <table> TO <user>` | Grant permissions to a user |
| `REVOKE PERMISSIONS ON <table> FROM <user>` | Revoke permissions from a user |

## Transaction Control Language (TCL)

| Command | Description |
| --- | --- |
| `BEGIN TRANSACTION` | Start a new transaction |
| `COMMIT` | Save changes to the database |
| `ROLLBACK` | Discard changes to the database |
| `SAVEPOINT <savepoint>` | Create a savepoint in a transaction |
| `ROLLBACK TO SAVEPOINT <savepoint>` | Rollback to a savepoint in a transaction |
| `RELEASE SAVEPOINT <savepoint>` | Remove a savepoint in a transaction |

## System Commands

| Command | Description |
| --- | --- |
| `SHOW DATABASES` | List all databases |
| `SHOW TABLES` | List all tables in the current database |
| `SHOW COLUMNS FROM <table>` | List all columns in a table |
| `SHOW INDEXES FROM <table>` | List all indexes in a table |
| `SHOW CREATE TABLE <table>` | Show the SQL statement that creates a table |
| `DESCRIBE <table>` | Show the structure of a table |
| `EXPLAIN SELECT * FROM <table>` | Show the execution plan of a query |
| `SET autocommit = 0` | Disable autocommit mode |
| `SET autocommit = 1` | Enable autocommit mode |
| `SET FOREIGN_KEY_CHECKS = 0` | Disable foreign key checks |

## User Commands

| Command | Description |
| --- | --- |
| `CREATE <user> '<user>'@'<host>' IDENTIFIED BY '<password>'` | Create a new user |
| `DROP <user> '<user>'@'<host>'` | Delete a user |
| `ALTER <user> '<user>'@'<host>' IDENTIFIED BY '<password>'` | Change password for a user |
| `GRANT ALL PRIVILEGES ON <db> TO '<user>'@'<host>'` | Grant all privileges to a user |
| `REVOKE ALL PRIVILEGES ON <db> FROM '<user>'@'<host>'` | Revoke all privileges from a user |
| `FLUSH PRIVILEGES` | Reload privileges from the grant tables |
