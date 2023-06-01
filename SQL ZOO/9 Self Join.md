
![](src/Pasted%20image%2020230531112230.png)

Schema

1.

How many **stops** are in the database.

```sql
select count(*)
from stops


```

![](src/Pasted%20image%2020230531112324.png)

2.

Find the **id** value for the stop 'Craiglockhart'

```sql
select id
from stops
where name =  'Craiglockhart'


```

![](src/Pasted%20image%2020230531112421.png)

3.

Give the **id** and the **name** for the **stops** on the '4' 'LRT' service.

```sql

select id, name
from stops
join route
   on id=stop
where company = 'LRT' 
and num = '4'

```

![](src/Pasted%20image%2020230531112752.png)


4.

The query shown gives the number of routes that visit either London Road (149) or Craiglockhart (53). Run the query and notice the two services that link these **stops** have a count of 2. Add a HAVING clause to restrict the output to these two routes.

```sql

SELECT company, num, COUNT(*)
FROM route WHERE stop=149 OR stop=53
GROUP BY company, num
having count(*) > 1

```

![](src/Pasted%20image%2020230531112853.png)

5.

Execute the self join shown and observe that b.stop gives all the places you can get to from Craiglockhart, without changing routes. Change the query so that it shows the services from Craiglockhart to London Road.

```sql
SELECT a.company, a.num, a.stop, b.stop
FROM route a JOIN route b ON
  (a.company=b.company AND a.num=b.num)
WHERE a.stop=53 and b.stop =149


```

![](src/Pasted%20image%2020230531113132.png)

6.

The query shown is similar to the previous one, however by joining two copies of the **stops** table we can refer to **stops** by **name** rather than by number. Change the query so that the services between 'Craiglockhart' and 'London Road' are shown. If you are tired of these places try 'Fairmilehead' against 'Tollcross'

```sql

SELECT a.company, a.num, stopa.name, stopb.name
FROM route a JOIN route b ON
  (a.company=b.company AND a.num=b.num)
  JOIN stops stopa ON (a.stop=stopa.id)
  JOIN stops stopb ON (b.stop=stopb.id)
WHERE stopa.name='Craiglockhart' and stopb.name = 'London Road'

```

![](src/Pasted%20image%2020230531113559.png)

7.

Give a list of all the services which connect stops 115 and 137 ('Haymarket' and 'Leith')

```sql
SELECT distinct a.company, a.num
FROM route a JOIN route b ON
  (a.company=b.company AND a.num=b.num)
  JOIN stops stopa ON (a.stop=stopa.id)
  JOIN stops stopb ON (b.stop=stopb.id)
WHERE a.stop=115 and b.stop =137


```

![](src/Pasted%20image%2020230531114025.png)

8.

Give a list of the services which connect the **stops** 'Craiglockhart' and 'Tollcross'

```sql
SELECT distinct a.company, a.num
FROM route a JOIN route b ON
  (a.company=b.company AND a.num=b.num)
  JOIN stops stopa ON (a.stop=stopa.id)
  JOIN stops stopb ON (b.stop=stopb.id)
WHERE stopa.name='Craiglockhart' and stopb.name = 'Tollcross'


```

![](src/Pasted%20image%2020230531114143.png)


9.

Give a distinct list of the **stops** which may be reached from 'Craiglockhart' by taking one bus, including 'Craiglockhart' itself, offered by the LRT company. Include the company and bus no. of the relevant services.

```sql
SELECT DISTINCT name, a.company, a.num
FROM route a
JOIN route b ON (a.company = b.company AND a.num = b.num)
JOIN stops ON a.stop = stops.id
WHERE b.stop = 53;


```

![](src/Pasted%20image%2020230531114949.png)

Find the routes involving two buses that can go from **Craiglockhart** to **Lochend**.  
Show the bus no. and company for the first bus, the name of the stop for the transfer,  
and the bus no. and company for the second bus.

Hint

Self-join twice to find buses that visit Craiglockhart and Lochend, then join those on matching stops.



```sql
```sql
SELECT S.num, S.company, S.name, T.num, T.company 
FROM 
    (SELECT DISTINCT a.num, a.company, sb.name 
     FROM route a JOIN route b ON (a.num = b.num and a.company = b.company) 
                  JOIN stops sa ON sa.id = a.stop 
                  JOIN stops sb ON sb.id = b.stop 
     WHERE sa.name = 'Craiglockhart' AND sb.name <> 'Craiglockhart'
)S

JOIN

    (SELECT x.num, x.company, sy.name 
     FROM route x JOIN route y ON (x.num = y.num and x.company = y.company) 
                  JOIN stops sx ON sx.id = x.stop 
                  JOIN stops sy ON sy.id = y.stop 
     WHERE sx.name = 'Lochend' AND sy.name <> 'Lochend'
    )T

ON (S.name = T.name)
ORDER BY S.num, S.name, T.num
```

source: https://stackoverflow.com/questions/27242351/find-the-routes-involving-two-buses-that-can-go-from-a-to-b

![](src/Pasted%20image%2020230531120948.png)

explanation: The first temp result, 'S' was a look for every stop that is reached from Craiglockhart. The second one, 'T,' is similar but all stops hit from Lochend. The results are joined with the 'ON' saying connect where the stops from Craiglockhart match those from Lochend, and that's your route. Finally, with the join on 'S' and 'T' get the numbers, companies, and the the name of the stop where you transfer. It's pretty clever.