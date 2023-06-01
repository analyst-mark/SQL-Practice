![](src/Pasted%20image%2020230529111352.png)
Schema

  
1.

Change the query shown so that it displays Nobel prizes for 1950.

```sql
SELECT yr, subject, winner
  FROM nobel
 WHERE yr = 1950
```

![](src/Pasted%20image%2020230529111507.png)

2.

Show who won the 1962 prize for literature.


```sql
SELECT winner
  FROM nobel
 WHERE yr = 1962
   AND subject = 'literature'
```

![](src/Pasted%20image%2020230529111536.png)

3.

Show the year and subject that won 'Albert Einstein' his prize.

```sql
select yr,subject
from nobel
where winner = 'Albert Einstein'
```

![](src/Pasted%20image%2020230529111647.png)

4.

Give the name of the 'peace' winners since the year 2000, including 2000.

```sql
select winner
from nobel
where subject = 'Peace'
and yr >= 2000
```

![](src/Pasted%20image%2020230529111825.png)

5.

Show all details (**yr**, **subject**, **winner**) of the literature prize winners for 1980 to 1989 inclusive.

```sql
select *
from nobel
where yr between 1980 and 1989
and subject = 'Literature'
```

![](src/Pasted%20image%2020230529112322.png)

6.

Show all details of the presidential winners:

- Theodore Roosevelt
- Thomas Woodrow Wilson
- Jimmy Carter
- Barack Obama

```sql
SELECT * FROM nobel
 WHERE
   WINNER IN ('Theodore Roosevelt',
                 'Woodrow Wilson',
                  'Jimmy Carter', 'Barack Obama'
)
```

![](src/Pasted%20image%2020230529112649.png)


7.

Show the winners with first name John

```sql
select winner
from nobel
where winner like 'John%'
```

![](src/Pasted%20image%2020230529112810.png)

8.

Show the year, subject, and name of physics winners for 1980 together with the chemistry winners for 1984.

```sql
select *
from nobel
where (yr = 1980 and subject = 'Physics')
or ( yr = 1984 and subject ='Chemistry')
```

![](src/Pasted%20image%2020230529113049.png)

9.

Show the year, subject, and name of winners for 1980 excluding chemistry and medicine

```sql
select *
from nobel
where subject not in ('chemistry','medicine')
and yr=1980
```

![](src/Pasted%20image%2020230529113159.png)

10.

Show year, subject, and name of people who won a 'Medicine' prize in an early year (before 1910, not including 1910) together with winners of a 'Literature' prize in a later year (after 2004, including 2004)


```sql
select *
from nobel
where (subject = 'Medicine' and yr < 1910)
or ( subject = 'Literature' and yr>= 2004)
```

![](src/Pasted%20image%2020230529113337.png)

## Harder Questions

11.

Find all details of the prize won by PETER GRÜNBERG

Non-ASCII characters

The u in his name has an **umlaut**. You may find this link useful [https://en.wikipedia.org/wiki/%C3%9C#Keyboarding](https://en.wikipedia.org/wiki/%C3%9C#Keyboarding)

```sql
SELECT *
FROM nobel
WHERE winner LIKE '%Peter Gr%nberg';
```

![](src/Pasted%20image%2020230529113537.png)

12.

Find all details of the prize won by EUGENE O'NEILL

Escaping single quotes

You can't put a single quote in a quote string directly. You can use two single quotes within a quoted string.


```sql
SELECT *
FROM nobel
WHERE winner LIKE '%EUGENE O%NEILL';
```

![](src/Pasted%20image%2020230529113640.png)

13.

Knights in order

List the winners, year and subject where the winner starts with **Sir**. Show the the most recent first, then by name order.


```sql
select winner,yr,subject
from nobel
where winner like 'Sir%'
order by yr desc ,winner
```

![](src/Pasted%20image%2020230529113842.png)

14.

The expression **subject IN ('chemistry','physics')** can be used as a value - it will be **0** or **1**.

Show the 1984 winners and subject ordered by subject and winner name; but list chemistry and physics last.


```sql
SELECT winner, subject
FROM nobel
where yr = 1984
order by case 
         when subject in ('chemistry','physics') then 0 else 1 
       end  desc ,
       subject,
       winner
```

![](src/Pasted%20image%2020230529114609.png)

