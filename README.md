# :minidisc: SQL Note

# :page_with_curl: SELECT 

```sql
SELECT column_name1, column_name2,...
FROM Table_name;
```

Here column_name1, column_name2,... are attributes of tables you want to select. 
If you want to select all the column from Table, use the following syntax:

```sql
SELECT * 
FROM Table_name;
```

Example: 
```sql
SELECT CustomerName, City 
FROM Customers;
```

![](select.JPG)

## :fast_forward: Select Distinct

Syntax:
```sql
SELECT DISTINCT column1, column2,...
FROM table_name;
```

Example:
```sql
SELECT DISTINCT Country
FROM Customers;
```

# :page_with_curl: WHERE Clause

Syntax:
```sql
SELECT column1, column2,...
FROM table_name;
WHERE condition
```

Example:
```sql
SELECT Country
FROM Customers;
WHERE Country = "Mexico";
```

### Operators for WHERE Clause:

![](where.JPG)


## :fast_forward: AND, OR and NOT Operator

- WHERE clauses can have a combination of AND, OR and NOT operator.

- AND operator display the result if both side of the operator is true
- OR operator display the result if anyone side is true.
- NOT operator display the result if condition is NOT TRUE.

### :arrow_right_hook: AND Operator Syntax:
```sql
SELECT column1, column2,...
FROM table_name;
WHERE condition AND condition2 AND condition3,...;
```

Example:
```sql
SELECT * FROM Customers
WHERE Country='Germany' AND City='Berlin';
```
### :arrow_right_hook: OR Operator Syntax:
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 OR condition2 OR condition3 ...;
```

Example:
```sql
SELECT * FROM Customers
WHERE City='Berlin' OR City='München';
```
### :arrow_right_hook: NOT Operator Syntax:
```sql
SELECT column1, column2, ...
FROM table_name
WHERE NOT condition;
```

Example:
```sql
SELECT * FROM Customers
WHERE NOT Country='Germany';
```

### :arrow_right_hook: Combination of AND and OR operator:

```sql
SELECT * FROM Customers
WHERE Country='Germany' AND (City='Berlin' OR City='München');
```
RESULT:

![](andOR.jpg)


# :page_with_curl: ORDER BY 

ORDER BY keyword is used to sort the result by ascending (ASC) or descending (DESC) 

### ORDER BY Syntax:

```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;
```
Example: by default ORDER BY is ascending (ASC)
```sql
SELECT * FROM Customers
ORDER BY Country;
```
Example: Descending
```sql
SELECT * FROM Customers
ORDER BY Country DESC;
```

### :fast_forward: ORDER BY multiple columns:

- With multiple columns, it means that first column will be sorted and if there are any same value then it will use next column to sort it. 

Example: First it orders by Country, but if some rows have the same Country, it orders them by CustomerName
```sql
SELECT * FROM Customers
ORDER BY Country, CustomerName;
```
# :page_with_curl: INSERT INTO

INSERT INTO is used to insert new record into the table


###  :fast_forward: INSERT INTO Syntax:
- There are TWO ways
  
:arrow_right_hook: First one: Using both column name and values to be inserted

```sql
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```
Example: Mention both column and value to be inserted
```sql
INSERT INTO Customers (CustomerName, ContactName, Address, City, PostalCode, Country)
VALUES ('Cardinal', 'Tom B. Erichsen', 'Skagen 21', 'Stavanger', '4006', 'Norway');
```
 
:arrow_right_hook: Second one: Using only values to insert it in to all column. Order of values matters

```sql
INSERT INTO table_name
VALUES (value1, value2, value3, ...);
```
