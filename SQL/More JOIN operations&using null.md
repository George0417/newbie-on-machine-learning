### More JOIN

**tables movie , actor and casting **
```
movie       	actor	    casting
id	             id	    movieid
title        	name	    actorid
yr	      	                ord
director	 	 
budget	 	 
gross	 	 

```


**Q1:The cast list is the names of the actors who were in the movie.

Use movieid=11768, (or whatever value you got from the previous question)**

```
select name from actor inner join movie on movie.id=11768 inner join casting on actor.id=casting.actorid and movie.id=casting.movieid
```

### using null
**Tbale of teacher**

```
id	dept	name	phone	mobile
101	1	Shrivell	2753	07986 555 1234
102	1	Throd	2754	07122 555 1920
103	1	Splint	2293	 
104	 	Spiregrain	3287	 
105	2	Cutflower	3212	07996 555 6574
106	 	Deadyawn	3345	 
```

**table of dept**
```
id	name
1	Computing
2	Design
3	Engineering

```

**Q1:List the teachers who have NULL for their department.**
```
select name from teacher 
where dept is null
```

**Q2:Use a different JOIN so that all teachers are listed.**

```
SELECT teacher.name, dept.name
 FROM teacher left JOIN dept
           ON (teacher.dept=dept.id)
```

>A left join B,the list is based on A

**Q3:Use COALESCE to print the mobile number. Use the number '07986 444 2266' if there is no number given. Show teacher name and mobile number or '07986 444 2266'**
>COALESCE(x,y,z) = x if x is not NULL
>COALESCE(x,y,z) = y if x is NULL and y is not NULL
>COALESCE(x,y,z) = z if x and y are NULL but z is not NULL
>COALESCE(x,y,z) = NULL if x and y and z are all NULL

>COALESCE(party,'None') AS aff
```
select name,coalesce (mobile,'07986 444 2266') from teacher
```

**Q4:Use COUNT and GROUP BY dept.name to show each department and the number of staff. Use a RIGHT JOIN to ensure that the Engineering department is listed.**
```
select dept.name,count(teacher.name) from teacher right join dept on teacher.dept=dept.id
group by dept.name
```

**Q5:Use CASE to show the name of each teacher followed by 'Sci' if the teacher is in dept 1 or 2 and 'Art' otherwise.**
```
select name,
case when dept in(1,2) then 'Sci'
else 'Art' end
from teacher

```

**Q6:Use CASE to show the name of each teacher followed by 'Sci' if the teacher is in dept 1 or 2, show 'Art' if the teacher's dept is 3 and 'None' otherwise**
```
select name,
case when dept in(1,2) then 'Sci'
 when dept=3 then 'Art'
else 'None' end
from teacher

```


