# PostgreSQL Tutorial

PostgreSQL is a free and open source advanced relational database system that supports both relational (SQL) and non-relational (JSON) queries.

# Table of Contents
- [Version](#version)
- [Database](#database)
    - [CREATE TABLE](#create-table)
    - [INSERT INTO](#insert-into)

# Version

```psql
SELECT version();
```
 
# Database

## CREATE TABLE

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

Insert Into Table:
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
