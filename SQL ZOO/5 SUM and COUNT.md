![](src/Pasted%20image%2020230530194329.png)
Schema

1.

Show the total **population** of the world.

world(**name**, **continent**, **area**, **population**, **gdp**)


```sql
SELECT SUM(population)
FROM world

```

2.

List all the continents - just once each.

```sql
SELECT distinct continent
FROM world

```

![](src/Pasted%20image%2020230530200612.png)

3.

Give the total GDP of Africa


```sql
select sum(gdp)
from world
where continent = 'Africa'

```

![](src/Pasted%20image%2020230530200659.png)

4.

How many countries have an **area** of at least 1000000

```sql
select count(name)
from world
where area >= 1000000

```


![](src/Pasted%20image%2020230530200756.png)


5.

What is the total **population** of ('Estonia', 'Latvia', 'Lithuania')

```sql
select sum(population)
from world
where name in ('Estonia', 'Latvia', 'Lithuania')

```

![](src/Pasted%20image%2020230530201051.png)

  
6.

For each **continent** show the **continent** and number of countries.

```sql
select continent , count(*)
from world
group by continent

```

![](src/Pasted%20image%2020230530201147.png)


7.

For each **continent** show the **continent** and number of countries with populations of at least 10 million.

```sql
select continent , count(*)
from world
where population >= 10000000
group by continent


```

![](src/Pasted%20image%2020230530201240.png)

8.

List the continents that **have** a total population of at least 100 million.


```sql
SELECT continent
FROM world
GROUP BY continent
HAVING SUM(population) > 100000000

```


```sql


```


```sql


```


```sql


```


```sql


```