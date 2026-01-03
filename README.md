# PostgreSQL Tutorial

A comprehensive guide and tutorial to postgresql.

PostgreSQL is a free and open source advanced relational database system that supports both relational (SQL) and non-relational (JSON) queries.

# Table of Contents
- [Version](#version)
- [Database](#database)
    - [CREATE TABLE](#create-table)
    - [INSERT INTO](#insert-into)
    - [Fetch Data](#fetch-data)
    - [ADD Column](#add-column)
    - [UPDATE](#update)
    - [DROP COLUMN](#drop-column)
    - [DELETE](#delete)
    - [DROP TABLE](#drop-table)

# Version

```psql
SELECT version();
```
 
# Database

## CREATE TABLE

To create a table in a database:
Use `CREATE TABLE` command.

Create Table:
```psql
CREATE TABLE cars (
  brand VARCHAR(255),
  model VARCHAR(255),
  year INT
);
```

Display Table:
```
SELECT * FROM cars;
```

## INSERT INTO

To insert data into a table:
Use `INSERT INTO` command.

Insert a Record Into Table:
```psql
INSERT INTO cars (brand, model, year)
VALUES ('Ford', 'Mustang', 1964);
```

Insert Multiple Rows Into Table:
```psql
INSERT INTO cars (brand, model, year)
VALUES
  ('Volvo', 'p1800', 1968),
  ('BMW', 'M1', 1978),
  ('Toyota', 'Celica', 1975);
```

Display Table:
```psql
SELECT * FROM cars;
```

## Fetch Data

To retrieve data in the database:
Use `SELECT` command.

SELECT Column:
```psql
SELECT brand, year FROM cars;
```

SELECT All:
```psql
SELECT * FROM cars;
```

## ADD Column

To add a column to an existing table:
Use `ALTER TABLE` command.

ADD Column:
```psql
ALTER TABLE cars
ADD color VARCHAR(255);
```

Display Table:
```psql
SELECT * FROM cars;
```

## UPDATE

To modify an existing data in a table:
Use `UPDATE` command.

Update a Record in Table:
```psql
UPDATE cars
SET color = 'red'
WHERE brand = 'Volvo';
```

Update Multiple Columns:
```psql
UPDATE cars
SET color = 'white', year = 1970
WHERE brand = 'Toyota';
```

Display Table:
```psql
SELECT * FROM cars;
```

## ALTER COLUMN

To modify a column in the table:
Use `ALTER COLUMN` command.

Alter Column:
```psql
ALTER TABLE cars
ALTER COLUMN year TYPE VARCHAR(4);
```

```psql
ALTER TABLE cars
ALTER COLUMN color TYPE VARCHAR(30);
```

## DROP COLUMN

To remove a column in the table:
Use `DROP COLUMN` command.

Drop Column:
```psql
ALTER TABLE cars
DROP COLUMN color;
```

Display Table:
```psql
SELECT * FROM cars;
```

## DELETE

To delete a record in the table:
Use `DELETE` command.

Delete Records:
```psql
DELETE FROM cars
WHERE brand = 'Volvo';
```

DELETE All Records:
```psql
DELETE FROM cars;
```

Truncate Table (Same as previous):
```psql
TRUNCATE TABLE cars;
```

Display Table:
```psql
SELECT * FROM cars;
```

## DROP TABLE

To drop an existing table in a database:
Use `DROP TABLE` command.

DROP TABLE:
```psql
DROP TABLE cars;
```

Display Table:
```psql
SELECT * FROM cars;
```
