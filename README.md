# SQL Note

# 1. Select Data from database

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

## Select Distinct

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

## WHERE Clause

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


## AND, OR and NOT Operator

- WHERE clauses can have a combination of AND, OR and NOT operator.

- AND operator display the result if both side of the operator is true
- OR operator display the result if anyone side is true.
- NOT operator display the result if condition is NOT TRUE.

### AND Operator Syntax:
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
### OR Operator Syntax:
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
### NOT Operator Syntax:
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

#### Combination of AND and OR operator:

```sql
SELECT * FROM Customers
WHERE Country='Germany' AND (City='Berlin' OR City='München');
```
RESULT:

![](andOR.jpg)


