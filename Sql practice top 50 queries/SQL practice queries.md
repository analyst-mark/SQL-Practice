
#### Q-1. Write an SQL query to fetch “FIRST_NAME” from the Worker table using the alias name <WORKER_NAME>.


```sql
select first_name as worker_name 
from worker
```

![](src/Pasted%20image%2020230525203317.png)

#### Q-2. Write an SQL query to fetch “FIRST_NAME” from the Worker table in upper case.

```sql
select upper(first_name)
from worker
```


![](src/Pasted%20image%2020230525203516.png)


#### Q-3. Write an SQL query to fetch unique values of DEPARTMENT from the Worker table.

```sql
select distinct DEPARTMENT
from worker
```

![](src/Pasted%20image%2020230525203701.png)

#### Q-4. Write an SQL query to print the first three characters of  FIRST_NAME from the Worker table.

```sql
select substring(first_name,1,3)
from worker
```

![](src/Pasted%20image%2020230525203829.png)

#### Q-5. Write an SQL query to find the position of the alphabet (‘a’) in the first name column ‘Amitabh’ from the Worker table.

```sql
select instr(first_name,binary'a') as  position
from worker
where FIRST_NAME = 'Amitabh'


```

![](src/Pasted%20image%2020230525204806.png)

**Notes.**

- The INSTR does a case-insensitive search.
- Using the BINARY operator will make INSTR work as the case-sensitive function.

#### Q-6. Write an SQL query to print the FIRST_NAME from the Worker table after removing white spaces from the right side.

```sql
select rtrim(first_name)
from worker

```

![](src/Pasted%20image%2020230525213939.png)

#### Q-7. Write an SQL query to print the DEPARTMENT from the Worker table after removing white spaces from the left side.

```sql
select ltrim(department)
from worker

```

![](src/Pasted%20image%2020230525214044.png)

#### Q-8. Write an SQL query that fetches the unique values of DEPARTMENT from the Worker table and prints its length.

```sql
select distinct department, length(department)
from worker
```

![](src/Pasted%20image%2020230525214212.png)

#### Q-9. Write an SQL query to print the FIRST_NAME from the Worker table after replacing ‘a’ with ‘A’.

```sql
select replace(first_name,'a','A')
from worker
```

![](src/Pasted%20image%2020230525214332.png)

#### Q-10. Write an SQL query to print the FIRST_NAME and LAST_NAME from the Worker table into a single column COMPLETE_NAME. A space char should separate them.

```sql
Select CONCAT(FIRST_NAME, ' ', LAST_NAME) AS complete_name
from Worker;
```

![](src/Pasted%20image%2020230525214500.png)

#### Q-11. Write an SQL query to print all Worker details from the Worker table order by FIRST_NAME Ascending.

```sql
Select * 
from Worker 
order by FIRST_NAME asc;
```

![](src/Pasted%20image%2020230525214556.png)

#### Q-12. Write an SQL query to print all Worker details from the Worker table order by FIRST_NAME Ascending and DEPARTMENT Descending.

```sql
Select * 
from Worker 
order by FIRST_NAME asc,department desc
```

![](src/Pasted%20image%2020230525214659.png)

#### Q-13. Write an SQL query to print details for Workers with the first names “Vipul” and “Satish” from the Worker table.

```sql
Select *
 from Worker
 where FIRST_NAME in ('Vipul','Satish')
```

![](src/Pasted%20image%2020230525214813.png)

#### Q-15. Write an SQL query to print details of Workers with DEPARTMENT name as “Admin”.

```sql
Select *
 from Worker
 where department = 'Admin'
```

![](src/Pasted%20image%2020230525214940.png)

#### Q-16. Write an SQL query to print details of the Workers whose FIRST_NAME contains ‘a’.

```sql
Select *
 from Worker
 where first_name like '%A%';
```

![](src/Pasted%20image%2020230525215317.png)

#### Q-17. Write an SQL query to print details of the Workers whose FIRST_NAME ends with ‘a’.

```sql
Select *
 from Worker
 where first_name like '%a';
```

![](src/Pasted%20image%2020230525215347.png)

#### Q-18. Write an SQL query to print details of the Workers whose FIRST_NAME ends with ‘h’ and contains six alphabets.

```sql
Select *
 from Worker
 where first_name like '______h';
```

![](src/Pasted%20image%2020230525215446.png)

#### Q-19. Write an SQL query to print details of the Workers whose SALARY lies between 100000 and 500000.

```sql
Select *
from Worker 
where SALARY between 100000 and 500000;
```

![](src/Pasted%20image%2020230525215530.png)

#### Q-20. Write an SQL query to print details of the Workers who joined in Feb’2014.

```sql
Select * 
from Worker 
where   year(JOINING_DATE) = 2014 
	and 
		month(JOINING_DATE) = 2;
```

![](src/Pasted%20image%2020230525215643.png)

#### Q-21. Write an SQL query to fetch the count of employees working in the department ‘Admin’.

```sql
SELECT COUNT(*) 
FROM worker 
WHERE DEPARTMENT = 'Admin';
```

![](src/Pasted%20image%2020230525215732.png)

#### Q-22. Write an SQL query to fetch worker names with salaries >= 50000 and <= 100000.

```sql
SELECT concat(FIRST_NAME, ' ' , last_name) full_name,SALARY
FROM worker 
WHERE Salary BETWEEN 50000 AND 100000
```

#### Q-23. Write an SQL query to fetch the no. of workers for each department in descending order.

```sql
SELECT DEPARTMENT, count(*) No_Of_Workers 
FROM worker 
GROUP BY DEPARTMENT 
ORDER BY No_Of_Workers DESC;
```

![](src/Pasted%20image%2020230525220216.png)

#### Q-24. Write an SQL query to print details of the Workers who are also Managers.

```sql
SELECT DISTINCT W.FIRST_NAME, T.WORKER_TITLE
FROM Worker W
INNER JOIN Title T
ON W.WORKER_ID = T.WORKER_REF_ID
AND T.WORKER_TITLE  = 'Manager';
```

![](src/Pasted%20image%2020230525220336.png)

#### Q-25. Write an SQL query to fetch duplicate records having matching data in some fields of a table.

```sql
SELECT WORKER_TITLE, AFFECTED_FROM, COUNT(*)
FROM Title
GROUP BY WORKER_TITLE, AFFECTED_FROM
HAVING COUNT(*) > 1;
```

![](src/Pasted%20image%2020230525220624.png)  

![](src/Pasted%20image%2020230525220645.png)

#### Q-26. Write an SQL query to show only odd rows from a table.

```sql
SELECT * 
FROM Worker 
WHERE MOD (WORKER_ID, 2) <> 0;

-- OR

SELECT * 
FROM Worker 
WHERE worker_id % 2 = 1;

```


![](src/Pasted%20image%2020230525221003.png)

#### Q-27. Write an SQL query to show only even rows from a table.

```sql
SELECT * 
FROM Worker 
WHERE worker_id % 2 = 0;
```

![](src/Pasted%20image%2020230525221044.png)

#### Q-28. Write an SQL query to clone a new table from another table.


```sql

-- create a new table name cloneWorker and copy the data from worker using select

CREATE TABLE cloneWorker SELECT * FROM worker;

--check if the data is copied
select * from cloneworker
```

![](src/Pasted%20image%2020230525222007.png)


#### Q-29. Write an SQL query to fetch intersecting records of two tables.

```sql
(SELECT * FROM Worker)
INTERSECT
(SELECT * FROM WorkerClone);
```

![](src/Pasted%20image%2020230525222637.png)
**notes:  The INTERSECT operator will return no rows if the two tables are identical.**
<details>

the `cloneWorker` table is an exact copy of the `worker` table. There are no rows in the `cloneWorker` table that are not also in the `worker` table. Therefore, the `INTERSECT` operator will return no rows.

If you want to compare the two tables, you can use the `EXCEPT` operator instead. The `EXCEPT` operator returns all the rows in the first table that are not in the second table. For example, the following query will return all the rows in the `worker` table that are not in the `cloneWorker` table:

</details>

#### Q-30. Write an SQL query to show records from one table that another table does not have.

```sql
--add a new record to cloneworker

INSERT INTO cloneworker (worker_id, first_name,last_name,salary, joining_date,department)
VALUES (100, 'John', 'Doe', 100000, '2014-02-20','HR');

-- check the record  it added by using except

SELECT *
FROM cloneworker
EXCEPT
SELECT *
FROM worker;

--The `EXCEPT` operator will return all the rows in the first table that are not in the second table
```

![](src/Pasted%20image%2020230525224421.png)

![](src/Pasted%20image%2020230525224433.png)

#### Q-31. Write an SQL query to show the current date and time.

```sql
-- just show the date
SELECT CURDATE();

--show date and time

SELECT NOW();

```

![](src/Pasted%20image%2020230525224729.png)
![](src/Pasted%20image%2020230525224738.png)

#### Q-32. Write an SQL query to show the top n (say 10) records of a table.

```sql
SELECT first_name, salary
 FROM Worker 
 ORDER BY Salary DESC LIMIT 10;
```

![](src/Pasted%20image%2020230525224839.png)

#### Q-33. Write an SQL query to determine the nth (say n=5) highest salary from a table.

```sql
SELECT salary as fifth_highest_salary
FROM worker
ORDER BY salary DESC
LIMIT 5, 1;

/*This query will first order the `salary` column in descending order. Then, it will limit the results to the 5th row and the 1st column. This will return the 5th highest salary in the table.*/

--even though 90000  is the sixth record-- it is the fifth highest salary due to the duplicate 

-- use this to remove duplicates

SELECT DISTINCT salary as fifth_highest_salary 
FROM worker
ORDER BY salary DESC 
LIMIT 5, 1;


```
![](src/Pasted%20image%2020230525225729.png)

![](src/Pasted%20image%2020230525225850.png)

#### Q-34. Write an SQL query to determine the 5th highest salary without using the TOP or limit method.

```sql
-- select the salary, get the row number , order by desc
-- row number or rn , show the ranking in descending order
  SELECT salary,
         ROW_NUMBER() OVER (ORDER BY salary DESC) AS rn
  FROM worker
 
 SELECT salary
FROM (
  SELECT salary,
         ROW_NUMBER() OVER (ORDER BY salary DESC) AS rn
  FROM worker
) AS t
WHERE rn = 5;



--OR

SELECT Salary
FROM Worker W1
WHERE 4 = (
 SELECT COUNT( DISTINCT ( W2.Salary ) )
 FROM Worker W2
 WHERE W2.Salary >= W1.Salary
 );


--OR

select salary as fifth_highest_Salary
from (
select salary, 
		dense_rank() over (order by salary desc) as _rank
from worker
) as temp
where _rank = 5



```
![](src/Pasted%20image%2020230525232227.png)

![](src/Pasted%20image%2020230525232303.png)

![](src/Pasted%20image%2020230526093706.png)

![](src/Pasted%20image%2020230526093717.png)



#### Q-35. Write an SQL query to fetch the list of employees with the same salary.

```sql
Select distinct W.WORKER_ID, W.FIRST_NAME, W.Salary 
from Worker W, Worker W1 
where W.Salary = W1.Salary 
and W.WORKER_ID != W1.WORKER_ID;

/*`from Worker W, Worker W1` is a self join. A self join is a join where the same table is joined with itself. In this case, the `worker` table is joined with itself.

Self joins are often used to find relationships between rows in the same table. For example, you could use a self join to find all pairs of employees who have the same manager.
*/

-- create a self-join , check where the salary is the same and the worker_id is not the same
```

![](src/Pasted%20image%2020230525233049.png)

![](src/Pasted%20image%2020230525233059.png)

#### Q-37. Write an SQL query to show one row twice in the results from a table.

```sql
select FIRST_NAME, DEPARTMENT from worker W where W.DEPARTMENT='HR' 
union all 
select FIRST_NAME, DEPARTMENT from Worker W1 where W1.DEPARTMENT='HR';
```

#### Q-38. Write an SQL query to fetch intersecting records of two tables.

```sql
(SELECT * FROM Worker)
INTERSECT
(SELECT * FROM WorkerClone);
```

#### Q-39. Write an SQL query to fetch the first 50% of records from a table.

```sql
SELECT *
FROM WORKER
WHERE WORKER_ID <= (SELECT count(WORKER_ID)/2 from Worker);


--OR - limit Count(*)/2 does not work in my sql workbench
-- variable and subqueries not also not work


SELECT *
FROM worker
ORDER BY worker_id 
limit 4 offset 0

/*
- The `LIMIT` clause is used to limit the number of rows that are returned by a query. 
- The `OFFSET` clause is used to skip the first n rows in the result set


`LIMIT` and `OFFSET` clauses are used to control the number of rows returned by a query and the starting point of the result set.

*/


```

![](src/Pasted%20image%2020230526095141.png)

#### Q-40. Write an SQL query to fetch the departments that have less than five people in them.

```sql
select department, count(*)
from worker
group by DEPARTMENT
having count(*) < 5

```

![](src/Pasted%20image%2020230526105640.png)

#### Q-41. Write an SQL query to show all departments along with the number of people in there. 

```sql
select department, count(*)
from worker
group by DEPARTMENT
```

![](src/Pasted%20image%2020230526123658.png)

#### Q-42. Write an SQL query to show the last record from a table.

```sql
Select * 
from Worker 
where 
	WORKER_ID = (SELECT max(WORKER_ID) from Worker);

--OR    
    
select *
from worker
order by worker_id desc
limit 1    
```

![](src/Pasted%20image%2020230526123900.png)

#### Q-43. Write an SQL query to fetch the first row of a table.

```sql
Select * 
from Worker 
where 
	WORKER_ID = (SELECT min(WORKER_ID) from Worker);
    
--OR


select *
from worker
order by worker_id 
limit 1    
```


![](src/Pasted%20image%2020230526123950.png)

#### Q-44. Write an SQL query to fetch the last five records from a table.


```sql
select *
from worker
order by WORKER_ID
limit 5 offset 3
```

![](src/Pasted%20image%2020230526124219.png)

#### Q-45. Write an SQL query to print the name of employees having the highest salary in each department.

```sql
select first_name,DEPARTMENT,salary
from worker 
where (department, salary) in (
  SELECT department, MAX(salary) AS salary
    FROM worker
    GROUP BY department)

--the subquery calculates the max salary of each department
-- there are 4 names in the result because there are 2 people witht the max salary in admin department 

```

![](src/Pasted%20image%2020230526125925.png)

![](src/Pasted%20image%2020230526125936.png)

#### Q-46. Write an SQL query to fetch three max salaries from a table.

```sql
select distinct salary
from worker
order by SALARY desc
limit 3
```

![](src/Pasted%20image%2020230526130318.png)

#### Q-47. Write an SQL query to fetch three min salaries from a table.

```sql
select distinct salary
from worker
order by SALARY 
limit 3
```

![](src/Pasted%20image%2020230526130350.png)

#### Q-48. Write an SQL query to fetch nth max salaries from a table.

```sql
select distinct salary
from worker
order by SALARY 
limit n

--change the n -- variable is not working in workbench
```

#### Q-49. Write an SQL query to fetch departments along with the total salaries paid for each of them.

```sql
SELECT DEPARTMENT, sum(Salary) 
from worker 
group by DEPARTMENT;
```

![](src/Pasted%20image%2020230526131004.png)

#### Q-50. Write an SQL query to fetch the names of workers who earn the highest salary.

```sql
SELECT FIRST_NAME, SALARY 
from Worker 
WHERE SALARY=
		(SELECT max(SALARY) 
        from Worker);


--OR

SELECT first_name,salary
FROM worker
WHERE salary = (SELECT MAX(salary)
FROM worker);

```

![](src/Pasted%20image%2020230526131554.png)




