
## Select Statement

	The SELECT statement is used to select data from a database.

	The data returned is stored in a result table, called the result-set.


 ###  SELECT Syntax

```sql
SELECT column1, column2, ...
  FROM tablename;
```

Here, column1, column2, ... are the field names of the table you want to select data from. If you want to select all the fields available in the table, use the following syntax:

```sql
SELECT * FROM tablename;
```


## SQL INSERT Statement

	INSERT INTO statement is used to insert new records in a table.

### INSERT INTO Syntax
	It is possible to write the INSERT INTO statement in two ways:

1. Specify both the column names and the values to be inserted:
	```sql
	INSERT INTO tablename (column1, column2, column3, ...)
    VALUES (value1, value2, value3, ...);
```

2. If you are adding values for all the columns of the table, you do not need to specify the column names in the SQL query. However, make sure the order of the values is in the same order as the columns in the table. Here, the INSERT INTO syntax would be as follows:

	```sql
	INSERT INTO tablename
    VALUES (value1, value2, value3, ...);
	```

### INSERT INTO Example

	The following SQL statement inserts a new record in the patients table:

```sql
-- Insert a record
INSERT INTO patients (first_name, last_name, gender, birth_date, city, province_id, allergies, weight, height)
    VALUES ('John', 'Smith', 'M', '1994-02-21', 'Hamilton','ON', NULL, 132, 182);
 
-- Select the most recent record by id to display it.
select * from patients
	where patient_id = (select max(patient_id) from patients);
```


### Insert Data Only in Specified Columns

It is also possible to only insert data in specific columns.

If the table column allow for NULL values then you do not need to include the column in your insert statement.

The following SQL statement will insert a new record, but only insert data in the "first_name", "last_name", and "gender" columns (patient_id will be updated automatically):

```sql
-- Insert a record
INSERT INTO patients (first_name, last_name, gender)
    VALUES ('Jane', 'Doe','F');
    
-- Select the most recent record by id to display it.
select * from patients
	where patient_id = (select max(patient_id) from patients);
```

## SQL DELETE Statement

	The DELETE statement is used to delete existing records in a table 


### DELETE Syntax

```sql
DELETE FROM tablename WHERE condition;
```

### SQL DELETE Example

The following SQL statement deletes all patients named "Paul" from the "patients" table:

```sql
DELETE FROM patients WHERE first_name = 'Paul';

-- There are no longer any patients named 'Paul' in the database
select * from patients where first_name = 'Paul'

```


## SQL UPDATE Statement

The UPDATE statement is used to modify the existing records in a table.

### UPDATE Syntax

```sql
UPDATE tablename
    SET column1 = value1, column2 = value2, ...
    WHERE condition;
```

Note: Be sure to specify the where clause. Failing to include the where clause will result in all of the rows to be updated.

The following SQL statement updates the first patient (patient_id = 1) with a new first_name and a new weight.

```sql
UPDATE patients
SET
  first_name = 'John',
  weight = 120
WHERE patient_id = 1;

-- display the patient we just updated
select * from patients where patient_id = 1
```


### UPDATE Multiple Records

It is the WHERE clause that determines how many records will be updated.

The following SQL statement will update the allergies to 'NKA' (no known allergies) for all records where allergies is NULL

```sql
UPDATE patients
SET allergies = 'NKA'
WHERE allergies is NULL;

-- display the patients table
select * from patients;
```



