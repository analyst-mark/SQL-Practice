
![](src/Pasted%20image%2020230530211859.png)
Schema

1.

List the films where the **yr** is 1962 [Show id ,title]

```sql
SELECT id, title
 FROM movie
 WHERE yr=1962

select title
from casting
join movie m
on m.id = movieid
where m.id in (SELECT id, title
 FROM movie
 WHERE yr=1978)
group by movieid
```

![](src/Pasted%20image%2020230530214256.png)

2.

Give year of 'Citizen Kane'.

```sql
SELECT yr
 FROM movie
 WHERE title = 'Citizen Kane'

```

![](src/Pasted%20image%2020230530214344.png)

3.

List all of the Star Trek movies, include the **id**, **title** and **yr** (all of these movies include the words Star Trek in the title). Order results by year


```sql
select id,title,yr
from movie
where title like '%Star Trek%'
order by yr

```

![](src/Pasted%20image%2020230530214521.png)


4.

What **id** number does the actor 'Glenn Close' have?


```sql
select id
from actor
where name =  'Glenn Close'

```

![](src/Pasted%20image%2020230530214608.png)

5.

What is the **id** of the film 'Casablanca'

```sql
select id
from movie
where title =  'Casablanca'

```

![](src/Pasted%20image%2020230530214652.png)


6.

Obtain the cast list for 'Casablanca'.

what is a cast list?

Use **movieid=11768**, (or whatever value you got from the previous question)


```sql
select name
from actor
join casting
on actorid=id
where movieid = 27

```

![](src/Pasted%20image%2020230530214916.png)


7.

Obtain the cast list for the film 'Alien'


```sql
select name
from actor a
   join casting c
   on a.id= actorid
join movie m 
   on m.id = movieid
   where title = 'Alien'
```

![](src/Pasted%20image%2020230530215249.png)


8.

List the films in which 'Harrison Ford' has appeared

```sql
select title
from actor a
   join casting c
   on a.id= actorid
join movie m 
   on m.id = movieid

```

![](src/Pasted%20image%2020230530215427.png)


## Harrison Ford as a supporting actor

9.

List the films where 'Harrison Ford' has appeared - but not in the starring role. 
[Note: the **ord** field of casting gives the position of the actor. If ord=1 then this actor is in the starring role]


```sql
select title
from actor a
   join casting c
   on a.id= actorid
join movie m 
   on m.id = movieid
   where name =  'Harrison Ford' 
   and ord != 1

```

![](src/Pasted%20image%2020230530220728.png)

10.

List the films together with the leading star for all 1962 films.


```sql
select title, name
from casting c
join actor a
on a.id = actorid
join movie m
on m.id = movieid
where ord=1
and yr = 1962

```

![](src/Pasted%20image%2020230530221420.png)

11.

Which were the busiest years for 'Rock Hudson', show the year and the number of movies he made each year for any year in which he made more than 2 movies.

```sql
SELECT yr,COUNT(title) 
FROM   movie 
JOIN casting 
	ON movie.id=movieid
JOIN actor  
	ON actorid=actor.id
WHERE name='Doris Day'
GROUP BY yr
HAVING COUNT(title) > 1

```

12.

List the film title and the leading actor for all of the films 'Julie Andrews' played in.

Did you get "Little Miss Marker twice"?


```sql

SELECT movieid FROM casting
WHERE actorid IN (
  SELECT id FROM actor
  WHERE name='Julie Andrews')
--- inner query  list he movies she participated


select title, name
from casting c
join actor a
on a.id = actorid
join movie m
on m.id = movieid
where ord=1
and m.id  in (SELECT movieid FROM casting
WHERE actorid IN (
  SELECT id FROM actor
  WHERE name='Julie Andrews'))
```

![](src/Pasted%20image%2020230530222239.png)

13.

Obtain a list, in alphabetical order, of actors who've had at least 15 **starring** roles.


```sql
select actorid  --count(*) to check the number
from casting
group by actorid
having count(*) > 15
-- inner query list of actor with more than 15 participating roles

select  name 
from  actor a
join casting 
  on actorid = a.id
where a.id in (select actorid
from casting
where ord =1 
group by actorid
having count(*) >= 15)
group by name
order by name

--atleast mean >=

```

![](src/Pasted%20image%2020230530224459.png)


14.

List the films released in the year 1978 ordered by the number of actors in the cast, then by title.

```sql
SELECT title, COUNT(actorid) 
FROM casting
JOIN movie 
ON movieid = movie.id
WHERE yr = 1978
GROUP BY movieid, title
ORDER BY COUNT(actorid) DESC,title
  
  --do not need to group by just count the actor id

```

![](src/Pasted%20image%2020230530225752.png)


15.

List all the people who have worked with 'Art Garfunkel'.

```sql
select movieid 
                  from casting
                  join actor a
                      on  a.id = actorid
                    where name =  'Art Garfunkel'

--inner query get the list of all movies of art

select name
from casting 
join actor a
on a.id = actorid
where movieid in (select movieid 
                  from casting
                  join actor a
                      on  a.id = actorid
                    where name =  'Art Garfunkel')
and name != 'Art Garfunkel'
order by name

-- a secon condition is needed to exclude Art in the list


```


![](src/Pasted%20image%2020230530232605.png)