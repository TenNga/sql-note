# :minidisc: SQL Note
- SQL is use to handle data in database 

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





# :page_with_curl: NULL Value

NULL is value not like zero as it has no value at all. Optional fields in Database with no value has NULL.

### :fast_forward: NULL checker
- IS NULL
- IS NOT NULL

```sql
SELECT column_names
FROM table_name
WHERE column_name IS NULL;
```
:arrow_right_hook: Example: Result with all address with no value.
```sql
SELECT CustomerName, ContactName, Address
FROM Customers
WHERE Address IS NULL;
```






# :page_with_curl: UPDATE Statement

UPDATE is use to modify the existing data/records in a table

###  :fast_forward: UPDATE Syntax:
- Remember to use WHERE clauses to choose specific data.
- All data will be updated if you fails to mention/use WHERE clause. 

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```
:arrow_right_hook: Example: Updating record with CustomerID equals to 1
```sql
UPDATE Customers
SET ContactName = 'Alfred Schmidt', City= 'Frankfurt'
WHERE CustomerID = 1;
```






# :page_with_curl: DELETE Statement

DELETE is use to remove/delete record in the table.

###  :fast_forward: DELETE Syntax:
- Remember to use WHERE clauses to choose specific data.
- All data will be deleted if you fails to mention/use WHERE clause. 

```sql
DELETE FROM table_name WHERE condition;
```
:arrow_right_hook: Example: Deleting a record where CustomerName is equal to "Alfreds Futterkiste".
```sql
ELETE FROM Customers WHERE CustomerName='Alfreds Futterkiste';
```





# :page_with_curl: TOP, LIMIT or ROWNUM 

SELECT TOP is used to specify some number of record to return.

###  :fast_forward: SELECT TOP Syntax:
- Remember that SELECT TOP is not support in stall database sytems.

```sql
SELECT TOP number|percent column_name(s)
FROM table_name
WHERE condition;
```

###  :fast_forward: LIMIT Syntax:
- SELECT TOP is equit to LIMIT in MySQL

```sql
SELECT column_name(s)
FROM table_name
WHERE condition
LIMIT number;
```
###  :fast_forward: ROWNUM Syntax:
- SELECT TOP is equit to ROWNUM in Oracle

```sql
SELECT column_name(s)
FROM table_name
WHERE ROWNUM <= number;
```

:arrow_right_hook: Example: Three statement below will return same result.
- SQL
```sql
SELECT TOP 3 * FROM Customers;
```
- MySQL
```sql
SELECT * FROM Customers
LIMIT 3;
```
- Oracle
```sql
SELECT * FROM Customers
WHERE ROWNUM <= 3;
```
###  :fast_forward: TOP PERCENT example:
- Return percentage of record from the data.

:arrow_right_hook: Example: 
- From 12 customer record, only 50% will be return.
- Only 6 will return.

```sql
SELECT TOP 50 PERCENT * FROM Customers;
```

![](50percentCustomer.JPG)







# :page_with_curl: MIN() and MAX() Function

Min() and MAX() is a function that will return a MINIMUM/MAXIMUM value from a given column.

###  :fast_forward: MIN() Syntax:

```sql
SELECT MIN(column_name)
FROM table_name
WHERE condition;
```
:arrow_right_hook: Example: Return smallest price from price column.
```sql
SELECT MIN(Price) AS SmallestPrice
FROM Products;
```

###  :fast_forward: MAX() Syntax:

```sql
SELECT MAX(column_name)
FROM table_name
WHERE condition;
```
:arrow_right_hook: Example: Return largest price from price column.
```sql
SELECT MAX(Price) AS LargestPrice
FROM Products;
```








# :page_with_curl: COUNT(), AVG() and SUM() Function

The COUNT() function returns the number of rows that matches a specified criterion.

The AVG() function returns the average value of a numeric column.

The SUM() function returns the total sum of a numeric column.

###  :fast_forward: COUNT() Syntax:

```sql
SELECT COUNT(column_name)
FROM table_name
WHERE condition;
```

:arrow_right_hook: Example: Finds the number of products:
```sql
SELECT COUNT(ProductID)
FROM Products;
```