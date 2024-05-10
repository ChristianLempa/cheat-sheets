# SQL Cheat-Sheet

## Data Definition Language (DDL)

| Command | Description |
| --- | --- |
| `CREATE DATABASE DBNAME` | Create a new database |
| `DROP DATABASE DBNAME` | Delete a database |
| `CREATE TABLE TABLENAME (COLUMN1 TYPE, COLUMN2 TYPE)` | Create a new table |
| `DROP TABLE TABLENAME` | Delete a table |
| `ALTER TABLE TABLENAME ADD COLUMN COLUMNNAME TYPE` | Add a new column to a table |
| `ALTER TABLE TABLENAME DROP COLUMN COLUMNNAME` | Remove a column from a table |
| `ALTER TABLE TABLENAME RENAME COLUMN OLDNAME TO NEWNAME` | Rename a column in a table |
| `ALTER TABLE TABLENAME RENAME TO NEWNAME` | Rename a table |
| `TRUNCATE TABLE TABLENAME` | Remove all rows from a table |
| `CREATE INDEX INDEXNAME ON TABLENAME (COLUMN)` | Create an index on a table |
| `DROP INDEX INDEXNAME` | Remove an index from a table |

## Data Manipulation Language (DML)

| Command | Description |
| --- | --- |
| `INSERT INTO TABLENAME (COLUMN1, COLUMN2) VALUES (VALUE1, VALUE2)` | Insert a new row into a table |
| `SELECT * FROM TABLENAME` | Retrieve all rows from a table |
| `UPDATE TABLENAME SET COLUMN1 = VALUE1 WHERE COLUMN2 = VALUE2` | Update rows in a table |
| `DELETE FROM TABLENAME WHERE COLUMN = VALUE` | Delete rows from a table |

## Data Query Language (DQL)

| Command | Description |
| --- | --- |
| `SELECT COLUMN1, COLUMN2 FROM TABLENAME` | Retrieve specific columns from a table |
| `SELECT * FROM TABLENAME WHERE COLUMN = VALUE` | Retrieve rows that match a condition |
| `SELECT * FROM TABLENAME ORDER BY COLUMN` | Retrieve rows sorted by a column |
| `SELECT * FROM TABLENAME LIMIT N` | Retrieve the first N rows from a table |
| `SELECT * FROM TABLENAME OFFSET N` | Retrieve rows starting from the Nth row |
| `SELECT * FROM TABLENAME JOIN OTHERTABLE ON TABLENAME.COLUMN = OTHERTABLE.COLUMN` | Retrieve rows from two tables that match a condition |
| `SELECT * FROM TABLENAME UNION SELECT * FROM OTHERTABLE` | Retrieve rows from two tables without duplicates |
| `SELECT * FROM TABLENAME GROUP BY COLUMN` | Group rows that have the same value in a column |
| `SELECT * FROM TABLENAME HAVING COUNT(COLUMN) > N` | Filter grouped rows that have more than N rows |
| `SELECT * FROM TABLENAME WHERE COLUMN IN (VALUE1, VALUE2)` | Retrieve rows where a column value matches any value in a list |
| `SELECT * FROM TABLENAME WHERE COLUMN BETWEEN VALUE1 AND VALUE2` | Retrieve rows where a column value is within a range |
| `SELECT * FROM TABLENAME WHERE COLUMN LIKE 'VALUE%'` | Retrieve rows where a column value matches a pattern |
| `SELECT * FROM TABLENAME WHERE COLUMN IS NULL` | Retrieve rows where a column value is NULL |
| `SELECT * FROM TABLENAME WHERE COLUMN IS NOT NULL` | Retrieve rows where a column value is not NULL |

## Data Control Language (DCL)

| Command | Description |
| --- | --- |
| `GRANT PERMISSIONS ON TABLENAME TO USER` | Grant permissions to a user |
| `REVOKE PERMISSIONS ON TABLENAME FROM USER` | Revoke permissions from a user |

## Transaction Control Language (TCL)

| Command | Description |
| --- | --- |
| `BEGIN TRANSACTION` | Start a new transaction |
| `COMMIT` | Save changes to the database |
| `ROLLBACK` | Discard changes to the database |
| `SAVEPOINT NAME` | Create a savepoint in a transaction |
| `ROLLBACK TO SAVEPOINT NAME` | Rollback to a savepoint in a transaction |
| `RELEASE SAVEPOINT NAME` | Remove a savepoint in a transaction |

## System Commands

| Command | Description |
| --- | --- |
| `SHOW DATABASES` | List all databases |
| `SHOW TABLES` | List all tables in the current database |
| `SHOW COLUMNS FROM TABLENAME` | List all columns in a table |
| `SHOW INDEXES FROM TABLENAME` | List all indexes in a table |
| `SHOW CREATE TABLE TABLENAME` | Show the SQL statement that creates a table |
| `DESCRIBE TABLENAME` | Show the structure of a table |
| `EXPLAIN SELECT * FROM TABLENAME` | Show the execution plan of a query |
| `SET autocommit = 0` | Disable autocommit mode |
| `SET autocommit = 1` | Enable autocommit mode |
| `SET FOREIGN_KEY_CHECKS = 0` | Disable foreign key checks |

## User Commands

| Command | Description |
| --- | --- |
| `CREATE USER 'USER'@'HOST' IDENTIFIED BY 'PASSWORD'` | Create a new user |
| `DROP USER 'USER'@'HOST'` | Delete a user |
| `ALTER USER 'USER'@'HOST' IDENTIFIED BY 'PASSWORD'` | Change password for a user |
| `GRANT ALL PRIVILEGES ON DBNAME TO 'USER'@'HOST'` | Grant all privileges to a user |
| `REVOKE ALL PRIVILEGES ON DBNAME FROM 'USER'@'HOST'` | Revoke all privileges from a user |
| `FLUSH PRIVILEGES` | Reload privileges from the grant tables |
