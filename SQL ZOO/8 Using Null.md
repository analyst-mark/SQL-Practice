
![](src/Pasted%20image%2020230531092457.png)
Schema

1.

List the teachers who have NULL for their department.


```sql
select name
from teacher
where dept is null

```

![](src/Pasted%20image%2020230531105628.png)


2.

Note the INNER JOIN misses the teachers with no department and the departments with no teacher.

```sql
SELECT teacher.name, dept.name
 FROM teacher INNER JOIN dept
           ON (teacher.dept=dept.id)

```

![](src/Pasted%20image%2020230531105644.png)

3.

Use a different JOIN so that all teachers are listed.


```sql
SELECT teacher.name, dept.name
 FROM teacher left JOIN dept
           ON (teacher.dept=dept.id)

```

![](src/Pasted%20image%2020230531105712.png)

4.

Use a different JOIN so that all departments are listed.

```sql
SELECT teacher.name, dept.name
 FROM teacher right JOIN dept
           ON (teacher.dept=dept.id)

```

![](src/Pasted%20image%2020230531105755.png)

5.

Use COALESCE to print the mobile number. Use the number '07986 444 2266' if there is no number given. **Show teacher name and mobile number or '07986 444 2266'**

```sql
select name,coalesce( mobile, '07986 444 2266')
from teacher

-- coalesce put a default value in the record is null or empty
```

![](src/Pasted%20image%2020230531105929.png)



6.

Use the COALESCE function and a LEFT JOIN to print the teacher **name** and department name. Use the string 'None' where there is no department.

```sql
SELECT teacher.name, coalesce( dept.name , 'None') department
 FROM teacher left JOIN dept
           ON (teacher.dept=dept.id)

```

![](src/Pasted%20image%2020230531110130.png)

7.

Use COUNT to show the number of teachers and the number of mobile phones.


```sql
select count(name), count(mobile)
from teacher

```

![](src/Pasted%20image%2020230531110248.png)

8.

Use COUNT and GROUP BY **dept.name** to show each department and the number of staff. Use a RIGHT JOIN to ensure that the Engineering department is listed.


```sql
SELECT dept.name, count(teacher.dept)
 FROM teacher right JOIN dept
           ON (teacher.dept=dept.id)
group by dept.name

```

![](src/Pasted%20image%2020230531110829.png)

9.

Use CASE to show the **name** of each teacher followed by 'Sci' if the teacher is in **dept** 1 or 2 and 'Art' otherwise.

```sql
SELECT name, 
	CASE
		 WHEN dept IN (1,2) 
		 THEN 'Sci'
         ELSE 'Art'
     END
FROM teacher

```

![](src/Pasted%20image%2020230531111603.png)

10.

Use CASE to show the name of each teacher followed by 'Sci' if the teacher is in dept 1 or 2, show 'Art' if the teacher's dept is 3 and 'None' otherwise.

```sql
SELECT name, 
	CASE
		 WHEN dept IN (1,2)  THEN 'Sci'
		 when dept = 3 then 'Art'
         ELSE 'None'
     END
FROM teacher

```

![](src/Pasted%20image%2020230531112023.png)

![](src/Pasted%20image%2020230531112028.png)


