# SQL WHERE Clause Guide

## Overview
The `WHERE` clause in SQL is used to filter records based on specified conditions. It is commonly used in `SELECT`, `UPDATE`, `DELETE`, and `INSERT` statements to narrow down the results.

## Syntax
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

## Examples

### 1. Filtering by a Specific Value
Retrieve all cities in the "Asia" continent:
```sql
SELECT * FROM City
WHERE CountryCode IN (
    SELECT Code FROM Country
    WHERE Continent = 'Asia'
);
```

### 2. Using Comparison Operators
Find all countries with a population greater than 10 million:
```sql
SELECT Name, Population
FROM Country
WHERE Population > 10000000;
```

### 3. Using Logical Operators (`AND`, `OR`, `NOT`)
Find countries in Asia with a population greater than 50 million:
```sql
SELECT Name, Continent, Population
FROM Country
WHERE Continent = 'Asia' AND Population > 50000000;
```

### 4. Using `LIKE` for Pattern Matching
Find all cities starting with 'New':
```sql
SELECT Name FROM City
WHERE Name LIKE 'New%';
```

### 5. Using `IN` with a Subquery (Multiple Row Subquery)
Get all cities belonging to countries in Asia:
```sql
SELECT Name, CountryCode, Population
FROM City
WHERE CountryCode IN (
    SELECT Code FROM Country
    WHERE Continent = 'Asia'
);
```

### 6. Using `BETWEEN` for Range Filtering
Find countries with populations between 10 million and 50 million:
```sql
SELECT Name, Population
FROM Country
WHERE Population BETWEEN 10000000 AND 50000000;
```

### 7. Using `EXISTS` to Check for Data
Find countries that have at least one city with a population greater than 1 million:
```sql
SELECT Name
FROM Country c
WHERE EXISTS (
    SELECT 1 FROM City ci
    WHERE ci.CountryCode = c.Code
    AND ci.Population > 1000000
);
```

## Notes
- The `WHERE` clause **cannot** be used with aggregate functions like `SUM()`, `AVG()`, or `COUNT()`. Use `HAVING` instead.
- If comparing text values, make sure to use single quotes (`'value'`).
- `IN` is used for multiple row subqueries, while `=` is used for single row subqueries.

---

## 🔗 Additional Resources
- [SQL WHERE Clause Documentation](https://www.w3schools.com/sql/sql_where.asp)
- [SQL Operators](https://www.sqltutorial.org/sql-operators/)
- [Advanced SQL Queries](https://mode.com/sql-tutorial/)
