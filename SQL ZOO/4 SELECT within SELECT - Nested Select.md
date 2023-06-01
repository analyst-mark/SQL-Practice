## Using nested SELECT

1.

List each country in the same continent as 'Brazil'.


```sql
SELECT name
FROM world 
WHERE continent = 
(SELECT continent 
FROM world WHERE name = 'Brazil')
```

![](src/Pasted%20image%2020230529115406.png)
inner query

![](src/Pasted%20image%2020230529115421.png)
same continent as Brazil

![](src/Pasted%20image%2020230529115728.png)


![](src/Pasted%20image%2020230529115736.png)

2.

List each country and its continent in the same continent as 'Brazil' or 'Mexico'.

```sql
SELECT name, continent FROM world
WHERE continent IN
  (SELECT continent 
     FROM world WHERE name='Brazil'
                   OR name='Mexico')

```

![](src/Pasted%20image%2020230529115852.png)

![](src/Pasted%20image%2020230529115913.png)

## Subquery on the SELECT line

If you are certain that only one value will be returned you can use that query on the SELECT line

3.

Show the population of China as a multiple of the population of the United Kingdom


```sql
SELECT
 population/(SELECT population FROM world
             WHERE name='United Kingdom')
  FROM world
WHERE name = 'China'

```

![](src/Pasted%20image%2020230529120006.png)

![](src/Pasted%20image%2020230529120019.png)

4.

Show each country that has a population greater than the population of ALL countries in Europe.

Note that we mean greater than every single country in Europe; not the combined population of Europe.

```sql
SELECT name FROM world
 WHERE population > ALL
      (SELECT population FROM world
        WHERE continent='Europe')

```

![](src/Pasted%20image%2020230529120051.png)


# SELECT within SELECT Tutorial

1.

List each country **name** where the **population** is larger than that of 'Russia'.

world(name, continent, area, population, gdp)

```sql
SELECT name FROM world
  WHERE population >
     (SELECT population FROM world
      WHERE name='Russia')

```

![](src/Pasted%20image%2020230529120755.png)


  
1.

List each country **name** where the **population** is larger than that of 'Russia'.

world(name, continent, area, population, gdp)


```sql
SELECT name FROM world
  WHERE population >
     (SELECT population FROM world
      WHERE name='Russia')


```

![](src/Pasted%20image%2020230530110822.png)

2.

Show the countries in Europe with a per capita GDP greater than 'United Kingdom'.

```sql
select name
from world
where  continent= 'Europe'
 and
gdp/population > 
		( select gdp/population from world
         where name = 'United Kingdom')


```

![](src/Pasted%20image%2020230530111448.png)


3.

List the **name** and **continent** of countries in the continents containing either **Argentina** or **Australia**. Order by name of the country.


```sql
select name,continent
from world
where continent  in  
       (select continent
        from world
        where name in ('Argentina', 'Australia'))

```

![](src/Pasted%20image%2020230530114233.png)

4.

Which country has a population that is more than United Kingdom but less than Germany? Show the name and the population.


```sql
select name,population from world
where population > (select population from world where name ='United Kingdom')
and population < (select population from world where name ='Germany')

```

![](src/Pasted%20image%2020230530114523.png)


5.

Germany (population 80 million) has the largest population of the countries in Europe. Austria (population 8.5 million) has 11% of the population of Germany.

Show the name and the population of each country in Europe. Show the population as a percentage of the population of Germany.

The format should be _Name, Percentage_ for example:

|name|percentage|
|---|---|
|Albania|3%|
|Andorra|0%|
|Austria|11%|
|...|...|

Decimal places
Percent symbol %

```sql
select name,
		concat(
				round( 100 * population /
									(select population from world 
									where name = 'Germany'))
				, '%')

from world
where continent = 'Europe'

```

![](src/Pasted%20image%2020230530120308.png)

6.

Which countries have a GDP greater than every country in Europe? [Give the **name** only.] (Some countries may have NULL gdp values)

```sql
select name
from world
where gdp > all ( select gdp from world where continent = 'Europe')

```

![](src/Pasted%20image%2020230530120433.png)

7.

Find the largest country (by area) in each continent, show the **continent**, the **name** and the **area**:

```sql
SELECT continent, name, population FROM world x
  WHERE population >= ALL
    (SELECT population FROM world y
        WHERE y.continent=x.continent
          AND population>0)


```

![](src/Pasted%20image%2020230530120656.png)



```sql
SELECT continent, name,area FROM world x
  WHERE area >= ALL
    (SELECT area FROM world y
        WHERE y.continent=x.continent
          AND area>0)


```


alternative answer using max

```sql
SELECT x.continent, x.name, x.area
FROM world x
WHERE x.area = (SELECT MAX(y.area) FROM world y WHERE y.continent=x.continent AND y.area>0)

```

![](src/Pasted%20image%2020230530120938.png)

8.

List each continent and the name of the country that comes first alphabetically.


```sql
SELECT x.continent, x.name
FROM world x
WHERE x.name = (SELECT MIN(y.name) FROM world y WHERE y.continent=x.continent)


```

![](src/Pasted%20image%2020230530122100.png)

9.

Find the continents where all countries have a population <= 25000000. Then find the names of the countries associated with these continents. Show **name**, **continent** and **population**.

```sql
SELECT name, continent, population FROM world x
  WHERE 25000000 >= ALL(SELECT population
	                FROM world y
		        WHERE x.continent = y.continent
                        AND y.population>0);
```

![](src/Pasted%20image%2020230530122502.png)

10.

Some countries have populations more than three times that of all of their neighbours (in the same continent). Give the countries and continents.

```SQL
SELECT name, continent FROM world x
  WHERE population >= ALL(SELECT population*3
                         FROM world y
                         WHERE x.continent = y.continent
                         and y.name != x.name)
                     
```

The code uses a subquery to find the population of all neighboring countries in the same continent as the country in the outer query. The subquery multiplies the population of each neighboring country by 3 and returns the result. The `ALL` function in the outer query compares the population of the country in the outer query to all the values returned by the subquery. If the population of the country in the outer query is greater than all the values returned by the subquery, then that country and its continent are included in the result.

In simpler terms, this code finds countries where their population is more than three times that of all their neighbors (in the same continent) and returns their name and continent.