
The CASE statement goes through conditions and returns a value when the first condition is met (like an if-then-else statement). So, once a condition is true, it will stop reading and return the result. If no conditions are true, it returns the value in the ELSE clause.

If there is no ELSE part and no conditions are true, it returns NULL.

## CASE Syntax

```sql
CASE
      WHEN condition1 THEN result1
      WHEN condition2 THEN result2
      WHEN conditionN THEN resultN
      ELSE result
  END;
```

## SQL CASE Examples

The following SQL goes through conditions and returns a value when the first condition is met:

```sql
SELECT patient_id, height,
  CASE
      WHEN height > 175 THEN 'height is greater than 175'
      WHEN height = 175 THEN 'height is 175'
      ELSE 'height is under 175'
  END AS height_group
  FROM patients;
```


The following SQL will order the patients by allergies. However, if allergies is NULL, then order by patient_id:

```sql
SELECT patient_id, first_name, allergies
  FROM patients
  ORDER BY
  (CASE
      WHEN allergies IS NULL THEN first_name
      ELSE allergies
  END);
```


![](src/Pasted%20image%2020230527154227.png)

![](src/Pasted%20image%2020230527154449.png)



![](src/Pasted%20image%2020230527154637.png)






