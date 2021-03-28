# Postgres Cheatsheet

### Useful commands

*Start psql as user*
```sql
psql -U username
```

*Connect to specific db*
```sql
\c database_name;

```
*Quit psql*
```sql
\q
```

*List databases*
```sql
\l
```

*List all users*
```sql
\du
```
*List all schemas*
```sql
\dn
```

*List all stored procedures and functions*
```sql
\df
```

*List all tables in current database*
```sql
\dt
```
***
### Data types
```

bigint	int8	signed eight-byte integer
bigserial	serial8	autoincrementing eight-byte integer
bit [ (n) ]	 	fixed-length bit string
bit varying [ (n) ]	varbit [ (n) ]	variable-length bit string
boolean	bool	logical Boolean (true/false)
box	 	rectangular box on a plane
bytea	 	binary data ("byte array")
character [ (n) ]	char [ (n) ]	fixed-length character string
character varying [ (n) ]	varchar [ (n) ]	variable-length character string
cidr	 	IPv4 or IPv6 network address
circle	 	circle on a plane
date	 	calendar date (year, month, day)
double precision	float8	double precision floating-point number (8 bytes)
inet	 	IPv4 or IPv6 host address
integer	int, int4	signed four-byte integer
interval [ fields ] [ (p) ]	 	time span
json	 	textual JSON data
jsonb	 	binary JSON data, decomposed
line	 	infinite line on a plane
lseg	 	line segment on a plane
macaddr	 	MAC (Media Access Control) address
money	 	currency amount
numeric [ (p, s) ]	decimal [ (p, s) ]	exact numeric of selectable precision
path	 	geometric path on a plane
pg_lsn	 	PostgreSQL Log Sequence Number
point	 	geometric point on a plane
polygon	 	closed geometric path on a plane
real	float4	single precision floating-point number (4 bytes)
smallint	int2	signed two-byte integer
smallserial	serial2	autoincrementing two-byte integer
serial	serial4	autoincrementing four-byte integer
text	 	variable-length character string
time [ (p) ] [ without time zone ]	 	time of day (no time zone)
time [ (p) ] with time zone	timetz	time of day, including time zone
timestamp [ (p) ] [ without time zone ]	 	date and time (no time zone)
timestamp [ (p) ] with time zone	timestamptz	date and time, including time zone
tsquery	 	text search query
tsvector	 	text search document
txid_snapshot	 	user-level transaction ID snapshot
uuid	 	universally unique identifier
xml

```
***
### Create a database

```sql
CREATE DATABASE db_name;
```
***
### Creating Tables

Creating a table is as simple as using this syntax

```sql
CREATE TABLE table_name (
	column_name data_type PRIMARY KEY,
	column_name data_type,
	column_name data_type
)

```
***
### Drop
*Drop a database*
```sql
DROP DATABASE db_name;
```

*If you want to drop a table and it's dependent objects*
```sql
DROP TABLE table_name CASCADE;

```
***
### Alter
*Add a column*

```sql
ALTER TABLE table_name ADD COLUMN new_column_name TYPE;
```

*Drop a column*

```sql
ALTER TABLE table_name DROP COLUMN column_name;
```

*Rename a column*

```sql 
ALTER TABLE table_name RENAME column_name TO new_column_name;

```

*Add primary key to table*
```sql
ALTER TABLE table_name ADD PRIMARY KEY (column,...);
```
*Rename a table*

```sql
ALTER TABLE table_name RENAME TO new_table_name;
```
***
### Querying

*Select all from a table*
```sql
SELECT * FROM table_name;
```

*Specific column from table*
```sql
SELECT column_list
FROM table;
```

*Query data and select only unique rows*
```sql
SELECT DISTINCT (column)
FROM table;
```

*Filter*

```sql
SELECT *
FROM table
WHERE condition;
```

*Like operator, case-sensitive*
*ILike operator, not case-sensitive*
```sql
SELECT * FROM table_name
WHERE column LIKE '%value%'

SELECT * FROM table_name
WHERE column ILIKE '%value%'
```

*Between*
```sql
SELECT * FROM table_name
WHERE column BETWEEN low AND high;
```

*In*

```sql
SELECT * FROM table_name
WHERE column IN (value1, value2,...);
```

*Limit*

```sql
SELECT * FROM table_name
LIMIT limit OFFSET offset
ORDER BY column_name;
```

*Get number of rows in table*

```sql
SELECT COUNT (*)
FROM table_name;
```

*Sorting rows*
```sql
SELECT select_list
FROM table
ORDER BY column ASC [DESC], column2 ASC [DESC],...;
```

*Group by*

```sql
SELECT *
FROM table
GROUP BY column_1, column_2, ...;
```
***
### Modifying
```sql
INSERT INTO table(column1,column2,...)
VALUES(value_1,value_2,...);


INSERT INTO table_name(column1,column2,...)
VALUES(value_1,value_2,...),
      (value_1,value_2,...),
      (value_1,value_2,...)...

UPDATE table_name
SET column_1 = value_1,
    ...;

UPDATE table
SET column_1 = value_1,
    ...
WHERE condition;

DELETE FROM table_name;

DELETE FROM table_name
WHERE condition;
```
***
### Joins

```sql
SELECT * 
FROM table1
INNER JOIN table2 ON conditions

SELECT * 
FROM table1
LEFT JOIN table2 ON conditions

SELECT * 
FROM table1
FULL OUTER JOIN table2 ON conditions

SELECT * 
FROM table1
CROSS JOIN table2;

SELECT * 
FROM table1
NATURAL JOIN table2;
```
***
### Sets

```sql
SELECT * FROM table1
UNION
SELECT * FROM table2;

SELECT * FROM table1
EXCEPT
SELECT * FROM table2;

SELECT * FROM table1
INTERSECT
SELECT * FROM table2;
```
***

## Functions

## Managing Views
*Create a view*
```sql
CREATE OR REPLACE view_name AS
query;
```
***
## Stored procedures
***
## Triggers
***
## Indexes
***
## Nested Queries
***
