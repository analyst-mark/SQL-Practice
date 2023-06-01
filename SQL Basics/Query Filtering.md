# SQL AND, OR and NOT Operators

The WHERE clause can be combined with AND, OR, and NOT operators.

The AND and OR operators are used to filter records based on more than one condition:

- The AND operator displays a record if all the conditions separated by AND are TRUE.

- The OR operator displays a record if any of the conditions separated by OR is TRUE.

The NOT operator displays a record if the condition(s) is NOT TRUE.

## AND Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;
```

## OR Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 OR condition2 OR condition3 ...;
```

## NOT Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE NOT condition;
```

## AND Example

The following SQL statement selects all fields from "patients" where first_name is "John" AND city is "Toronto":

```sql
SELECT * FROM patients
WHERE first_name='John' AND city='Toronto';
```

## OR Example

The following SQL statement selects all fields from "patients" where city is "Hamilton" OR "Toronto":

```sql
SELECT * FROM patients
WHERE city='Hamilton' OR city='Toronto';
```

## NOT Example

The following SQL statement selects all fields from "patients" where province_id is NOT "ON" (Ontario):

```sql
SELECT * FROM patients
WHERE NOT province_id = 'ON';
```

# SQL ORDER BY Keyword

The ORDER BY keyword is used to sort the result-set in ascending or descending order.

The ORDER BY keyword sorts the records in ascending order by default. To sort the records in descending order, use the DESC keyword.

## ORDER BY Syntax

```sql
SELECT column1, column2, ...
    FROM table_name
    ORDER BY column1, column2, ... ASC|DESC;
```

ORDER BY Example The following SQL statement selects all patients from the "Patients" table, sorted by the "first_name" column:

```sql
SELECT * FROM patients
    ORDER BY first_name;
```

## ORDER BY DESC Example

The following SQL statement selects all patients from the "patients" table, sorted DESCENDING by the "first_name" column:

```sql
SELECT * FROM patients
    ORDER BY first_name DESC;
```

## ORDER BY Several Columns Example

The following SQL statement selects all patients from the "patients" table, sorted by the "first_name" and the "last_name" column. This means that it orders by first_name, but if some rows have the same first_name, it orders them by last_name:

```sql
SELECT * FROM patients
    ORDER BY first_name, last_name;
```

## ORDER BY Several Columns Example 2

The following SQL statement selects all patients from the "patients" table, sorted ascending by the "first_name" and descending by the "last_name" column:

```sql
SELECT * FROM patients
    ORDER BY first_name ASC, last_name DESC;
```

# SQL LIKE Operator

The LIKE operator is used in a WHERE clause to search for a specified pattern in a column.

There are two wildcards often used in conjunction with the LIKE operator:

- The percent sign (%) represents zero, one, or multiple characters

- The underscore sign (_) represents one, single character

The percent sign and the underscore can also be used in combinations

## LIKE Syntax

```sql
SELECT column1, column2, ...
  FROM table_name
  WHERE column LIKE pattern;
```

Here are some examples showing different LIKE operators with '%' and '_' wildcards:

![](src/Pasted%20image%2020230527151733.png)

## SQL LIKE Examples

The following SQL statement selects all patients with a first_name starting with "a":

```sql
SELECT * FROM patients
  WHERE first_name LIKE 'a%';
```

The following SQL statement selects all patients with a first_name ending with "a":

```sql
SELECT * FROM patients
  WHERE first_name LIKE '%a';
```

the following SQL statement selects all patients with a first_name that have "or" in any position:

```sql
SELECT * FROM patients
  WHERE first_name LIKE '%or%';
```

The following SQL statement selects all patients with a first_name that have "r" in the second position:

```sql
SELECT * FROM patients
  WHERE first_name LIKE '_r%';
```

The following SQL statement selects all patients with a first_name that starts with "a" and are at least 3 characters in length:

```sql
SELECT * FROM patients
  WHERE first_name LIKE 'a__%';
```

The following SQL statement selects all patients with a first_name that starts with "a" and ends with "o":

```
The following SQL statement selects all patients with a first_name that starts with "a" and ends with "o":
```

The following SQL statement selects all patients with a first_name that does NOT start with "a":

```sql
SELECT * FROM patients
  WHERE first_name NOT LIKE 'a%';
```

# SQL IN Operator

The IN operator allows you to specify multiple values in a WHERE clause.

The IN operator is a shorthand for multiple OR conditions.

## IN Syntax

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1, value2, ...);
```

or:

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name IN (SELECT STATEMENT);
```

## IN Operator Examples

The following SQL statement selects all patients that are located in "SK", "AB" or "MB":

```sql
SELECT * FROM patients
WHERE province_id IN ('SK', 'AB', 'MB');
```

The following SQL statement selects all patients that are NOT located in "SK", "AB" or "MB":

```sql
SELECT * FROM patients
WHERE province_id NOT IN ('SK', 'AB', 'MB');
```

The following SQL statement selects all patients that have the same first_name as a doctor.

```sql
SELECT * FROM patients 
WHERE first_name in (SELECT first_name FROM doctors)
-- Try running just the sub query to see the list
```

# SQL BETWEEN Operator

The BETWEEN operator selects values within a given range. The values can be numbers, text, or dates.

The BETWEEN operator is inclusive: begin and end values are included.

```sql
SELECT column_name(s) FROM table_name
  WHERE column_name BETWEEN value1 AND value2;
```

## NOT BETWEEN Example

To display the products outside the range of the previous example, use NOT BETWEEN:

```sql
SELECT * FROM patients
  WHERE weight NOT BETWEEN 100 AND 120;
```

## BETWEEN with IN Example

The following SQL statement selects all patients with a weight between 100 and 120. In addition; do not show patients located in 'ON', 'SK', or 'AB':

```sql
SELECT * FROM patients
  WHERE weight NOT BETWEEN 100 AND 120
  AND province_id NOT IN ('ON', 'SK', 'AB');
```

## Between with text

Text is compared based on the ASCII value of the text. For example, 'c'(99) is between 'a'(97) and 'e'(101) but 'C'(67) is not between 'a'(97) and 'e'(101).

The following SQL statement selects all patients with their first_name between 'Alex' and 'Ben'

```sql
SELECT * FROM patients
  WHERE first_name BETWEEN 'Alex' AND 'Ben'
```

![](src/Pasted%20image%2020230527153225.png)

# SQL GROUP BY Statement

The GROUP BY statement groups rows that have the same values into summary rows, like "find the number of patients in each province".

The GROUP BY statement is often used with aggregate functions (COUNT(), MAX(), MIN(), SUM(), AVG()) to group the result-set by one or more columns.

## GROUP BY Syntax

```sql
SELECT column_name(s)
  FROM table_name
  WHERE condition
  GROUP BY column_name(s)
```

## SQL GROUP BY Examples

The following SQL statement lists the number of patients in each province:

```sql
SELECT COUNT(*), province_id
  FROM patients
  GROUP BY province_id;
```

The following SQL statement lists the number of patients in each country, sorted high to low:

```sql
SELECT COUNT(*), province_id
  FROM patients
  GROUP BY province_id
  ORDER BY COUNT(*) DESC;
```

# SQL HAVING Clause

The HAVING clause was added to SQL because the WHERE keyword cannot be used with aggregate functions.

## HAVING Syntax

```sql
SELECT column_name(s)
  FROM table_name
  WHERE condition
  GROUP BY column_name(s)
  HAVING condition
  ORDER BY column_name(s);
```

## SQL HAVING Examples

The following SQL statement lists the names of patients with a common first_name (> 30 occurances).

```sql
SELECT COUNT(*), first_name
  FROM patients
  GROUP BY first_name
  HAVING count(*) > 30;
```

The following SQL statement lists the names of patients with a common first_name (> 30 occurances). Sorted high to low:

```sql
SELECT COUNT(*), first_name
  FROM patients
  GROUP BY first_name
  HAVING count(*) > 30
  ORDER BY COUNT(*) DESC;
```

# SQL SELECT DISTINCT Statement

The SELECT DISTINCT statement is used to return only distinct (different) values.

Inside a table, a column often contains many duplicate values; and sometimes you only want to list the different (distinct) values.

## SELECT DISTINCT Syntax

```sql
SELECT DISTINCT column1, column2, ...
  FROM table_name;
```

## SELECT Example Without DISTINCT

The following SQL statement selects all (including the duplicates) values from the first_name column in the patients table:

```sql
SELECT first_name FROM patients;
```

Now, let us use the SELECT DISTINCT statement and see the result.

## SELECT DISTINCT Examples

```sql
SELECT DISTINCT first_name FROM patients;
```

The following SQL statement lists the number of different (distinct) first_name:

```sql
SELECT COUNT(DISTINCT first_name) FROM patients;
```
# SQL ANY and ALL Operators

The ANY and ALL operators allow you to perform a comparison between a single column value and a range of other values.

**DISCLAIMER: This tool does not support the Any/All Operator.**

## The SQL ANY Operator

The ANY operator:

- returns a boolean value as a result

- returns TRUE if ANY of the subquery values meet the condition

ANY means that the condition will be true if the operation is true for any of the values in the range.

## ANY Syntax

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name operator ANY
  (SELECT column_name
  FROM table_name
  WHERE condition);
```

## The SQL ALL Operator

The ALL operator:

- returns a boolean value as a result

- returns TRUE if ALL of the subquery values meet the condition

- is used with SELECT, WHERE and HAVING statements

ALL means that the condition will be true only if the operation is true for all values in the range.

## ALL Syntax With SELECT

```sql
SELECT ALL column_name(s)

FROM table_name

WHERE condition;
```

## ALL Syntax With WHERE or HAVING

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name operator ALL
  (SELECT column_name
  FROM table_name
  WHERE condition);
```


# SQL IFNULL(), ISNULL(), COALESCE(), and NVL() Functions

The IFNULL function goes by many names depending on what language you are using. We use IFNULL but your specific language may use, ISNULL, COALESCE, or NVL but most function the same.

Look at the following SELECT statement:

```sql
select first_name, allergies from patients

```

The allergie column displays null for our output in some cases. We want it to display a default value in that case

![](src/Pasted%20image%2020230527171606.png)

# SQL NULL Values

## What is a NULL Value?

A field with a NULL value is a field with no value.

If a field in a table is optional, it is possible to insert a new record or update a record without adding a value to this field. Then, the field will be saved with a NULL value.

## How to Test for NULL Values?

It is not possible to test for NULL values with comparison operators, such as =, <, or <>.

We will have to use the IS NULL and IS NOT NULL operators instead.

### IS NULL Syntax

```sql
SELECT column_names
FROM table_name
WHERE column_name IS NULL;

```

### IS NOT NULL Syntax

```sql
SELECT column_names
FROM table_name
WHERE column_name IS NOT NULL;
```

## The IS NULL Operator

The IS NULL operator is used to test for empty values (NULL values).

The following SQL lists all patients with a NULL value in the "allergies" fie

```sql
SELECT *
FROM patients
WHERE allergies IS NULL;
```

![](src/Pasted%20image%2020230527171801.png)


![](src/Pasted%20image%2020230527171819.png)

![](src/Pasted%20image%2020230527171827.png)


![](src/Pasted%20image%2020230527171846.png)


![](src/Pasted%20image%2020230527171857.png)


![](src/Pasted%20image%2020230527171913.png)

![](src/Pasted%20image%2020230527171921.png)
```sql

```

```sql

```

```sql

```

```sql

```

```sql

```


```sql

```

```sql

```

```sql

```

```sql

```

```sql

```