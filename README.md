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
    - [Demo Database](./DEMO_DATABASE.md)
- [Syntax](#syntax)
    - [Operators](#operators)
    - [SELECT](#select)
    - [SELECT DISTINCT](#select-distinct)
    - [WHERE](#where)
    - [ORDER BY](#order-by)
    - [LIMIT](#limit)
    - [MIN and MAX](#min-and-max)
    - [COUNT](#count)
    - [SUM](#sum)
    - [AVG](#avg)
    - [LIKE](#like)
    - [IN](#in)
    - [BETWEEN](#between)
    - [AS](#as)
    - [Joins](#joins)
    - [INNER JOIN](#inner-join)
    - [LEFT JOIN](#left-join)
    - [RIGHT JOIN](#right-join)
    - [FULL JOIN](#full-join)
    - [CROSS JOIN](#cross-join)
    - [UNION](#union)
    - [GROUP BY](#group-by)
    - [HAVING](#having)
    - [EXISTS](#exists)
    - [ANY](#any)
    - [ALL](#all)
    - [CASE](#case)



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

# Syntax

## Operators

Here are the operators in the `WHERE` clause:
- Equal to `=`
- Less than `<`
- Greater than `>`
- Less than or equal to `<=`
- Greater than or equal to `>=`
- Not equal to `<>` or `!=`
- Check if a value matches a pattern (case-sensitive) `LIKE`
- Check if a value matches a pattern (case insensitive) `ILIKE`
- Logical AND: `AND`
- Logical OR: `OR`
- Check if a value is between a range of values `IN`
- Check if a value is between a range of values `BETWEEN`
- Check if a value is NULL: `IS NULL`
- Logical NOT: `NOT`

### Equal To
```psql
SELECT * FROM cars
WHERE brand = 'Volvo';
```

### Less Than
```psql
SELECT * FROM cars
WHERE year < 1975;
```

### Greater Than
```psql
SELECT * FROM cars
WHERE year > 1975;
```

### Less Than or Equal To
```psql
SELECT * FROM cars
WHERE year <= 1975;
```

### Greater Than or Equal To
```psql
SELECT * FROM cars
WHERE year >= 1975;
```

### Not Equal To
```psql
SELECT * FROM cars
WHERE brand <> 'Volvo';
```
or
```psql
SELECT * FROM cars
WHERE brand != 'Volvo';
```

### LIKE
```psql
SELECT * FROM cars
WHERE model LIKE 'M%';
```

### ILIKE
```psql
SELECT * FROM cars
WHERE model ILIKE 'm%';
```

### AND
```psql
SELECT * FROM cars
WHERE brand = 'Volvo' AND year = 1968;
```

### OR
```psql
SELECT * FROM cars
WHERE brand = 'Volvo' OR year = 1975;
```

### IN
```psql
SELECT * FROM cars
WHERE brand IN ('Volvo', 'Mercedes', 'Ford');
```

### BETWEEN
```psql
SELECT * FROM cars
WHERE year BETWEEN 1970 AND 1980;
```

### IS NULL
```psql
SELECT * FROM cars
WHERE model IS NULL;
```

### NOT
NOT LIKE:
```psql
SELECT * FROM cars
WHERE brand NOT LIKE 'B%';
```

NOT ILIKE:
```psql
SELECT * FROM cars
WHERE brand NOT ILIKE 'b%';
```

NOT IN:
```psql
SELECT * FROM cars
WHERE brand NOT IN ('Volvo', 'Mercedes', 'Ford');
```

NOT BETWEEN
```psql
SELECT * FROM cars
WHERE year NOT BETWEEN 1970 AND 1980;
```

IS NOT NULL
```psql
SELECT * FROM cars
WHERE model IS NOT NULL;
```

## SELECT
Select a column
```psql
SELECT customer_name, country FROM customers;
```

Select all columns
```psql
SELECT * FROM customers;
```

## SELECT DISTINCT

Select distinct values from column
```psql
SELECT DISTINCT country FROM customers;
```

Count distinct values from column
```psql
SELECT COUNT(DISTINCT country) FROM customers;
```

## WHERE

`WHERE` is used to filter records that follow a specific condition.
```psql
SELECT * FROM customers
WHERE city = 'London';
```

Text Fields and Numeric Fields
```psql
SELECT * FROM customers
WHERE customer_id = 19;
```

Greater than
```psql
SELECT * FROM customers
WHERE customer_id > 80;
```

## ORDER BY

`ORDER BY` is used to sort data in ascending or descending order.
```psql
SELECT * FROM products
ORDER BY price;
```

Descending Order:
```psql
SELECT * FROM products
ORDER BY price DESC;
```

Sort alphabetically:
```psql
SELECT * FROM products
ORDER BY product_name;
```

Sort alphabetically descending:
```psql
SELECT * FROM products
ORDER BY product_name DESC;
```

## LIMIT

`LIMIT` is used to limit the maximum number of records.
```psql
SELECT * FROM customers
LIMIT 20;
```

`OFFSET` is used to specify where to start selecting records.
```psql
SELECT * FROM customers
LIMIT 20 OFFSET 40;
```

## MIN and MAX

`MIN` is used to get the smallest value of the selected columns.
```psql
SELECT MIN(price)
FROM products;
```

`MAX` is used to get the largest value of the selected columns.
```psql
SELECT MAX(price)
FROM products;
```

Set Column Name
When `MIN` or `MAX` is used by default the columns will be named `min` and `max`.
```psql
SELECT MIN(price) AS lowest_price
FROM products;
```

## COUNT
`COUNT` is used to get the number of rows that matches a specific condition.
```psql
SELECT COUNT(customer_id)
FROM customers;
```

## SUM
`SUM` is used to get the total sum of a numeric column.
```psql
SELECT SUM(quantity)
FROM order_details;
```

## AVG
`AVG` is used to get the average value of a numeric column.
```psql
SELECT AVG(price)
FROM products;
```

Specifying Decimal Places
```psql
SELECT AVG(price)::NUMERIC(10,2)
FROM products;
```

## LIKE

`LIKE` is used with `WHERE` to search for a specified pattern in a column.

`%` is used to represent zero, one or multiple exact characters.
`_` is used to represent one single wildcard character.


To get the records that start with a specific letter or phrase:
```psql
SELECT * FROM customers
WHERE customer_name LIKE 'A%';
```

To get the records that contain a specific letter or phrase:
```psql
SELECT * FROM customers
WHERE customer_name LIKE '%A%';
```

`ILIKE` is the same as `LIKE` but is case-insensitive.

To get records that ends with a specific letter or phrase:
```psql
SELECT * FROM customers
WHERE customer_name LIKE '%en';
```

To get records that have specific characters and wildcard characters:
```psql
SELECT * FROM customers
WHERE city LIKE 'L_nd__';
```

## IN

`IN` is used with `WHERE` to get a list of values.
```psql
SELECT * FROM customers
WHERE country IN ('Germany', 'France', 'UK');
```

`NOT IN` is used to get a list of values that are NOT any of the values in the list.
```psql
SELECT * FROM customers
WHERE country NOT IN ('Germany', 'France', 'UK');
```

IN(SELECT)
```psql
SELECT * FROM customers
WHERE customer_id IN (SELECT customer_id FROM orders);
```

NOT IN (SELECT)
```psql
SELECT * FROM customers
WHERE customer_id NOT IN (SELECT customer_id FROM orders);
```

## BETWEEN

`BETWEEN` is used to get values within a given range.
```psql
SELECT * FROM Products
WHERE Price BETWEEN 10 AND 15;
```

Can be used with Text
```psql
SELECT * FROM Products
WHERE product_name BETWEEN 'Pavlova' AND 'Tofu';
```

Can be used with ORDER BY
```psql
SELECT * FROM Products
WHERE product_name BETWEEN 'Pavlova' AND 'Tofu'
ORDER BY product_name;
```

Can be used with Dates
```psql
SELECT * FROM orders
WHERE order_date BETWEEN '2023-04-12' AND '2023-05-05';
```

## AS
`AS` is used for aliasing columns.
```psql
SELECT customer_id AS id
FROM customers;
```

It is optional
```psql
SELECT customer_id id
FROM customers;
```

Can be used to concatenate columns
```psql
SELECT product_name || ' ' || unit AS product
FROM products;
```

Can add spaces to the alias
```psql
SELECT product_name AS "My Great Products"
FROM products;
```

## Joins
`JOIN` is used to combine two or more tables based on a related column between them.

Example:
Look at the `products` table:
```
 product_id |  product_name  | category_id
------------+----------------+-------------
         33 | Geitost        |           4
         34 | Sasquatch Ale  |           1
         35 | Steeleye Stout |           1
         36 | Inlagd Sill    |           8
```

Look at the `categories` table:
```psql
 category_id | category_name
-------------+----------------
           1 | Beverages
           2 | Condiments
           3 | Confections
           4 | Dairy Products
```

They can be combined into one table:
```psql
SELECT product_id, product_name, category_name
FROM products
INNER JOIN categories ON products.category_id = categories.category_id;
```

Result:
```
product_id |  product_name  | category_name
------------+----------------+----------------
         33 | Geitost        | Dairy Products
         34 | Sasquatch Ale  | Beverages
         35 | Steeleye Stout | Beverages
         36 | Inlagd Sill    | Seafood
```

There are different types of joins:
- INNER JOIN: Returns records that have matching values in both tables
- LEFT JOIN: Returns all records from the left table, and the matched records from the right table
- RIGHT JOIN: Returns all records from the right table, and the matched records from the left table
- FULL JOIN: Returns all records when there is a match in either left or right table

