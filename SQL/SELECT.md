# Select

### TABLE
```
name	      continent	   area	    population	           gdp
Afghanistan	Asia	     652230	    25500100	    20343000000
Albania	    Europe	    28748	    2831741	      12960000000
Algeria	    Africa	   2381741	  37100000	    188681000000
Andorra	    Europe	      468	    78115	        3712000000
Angola	    Africa	   1246700	  20609294	    100990000000
....
```


**Q1:Show the name and the population for 'Sweden', 'Norway' and 'Denmark'**

```
SELECT name, population FROM world
  WHERE name IN ( 'Sweden', 'Norway', 'Denmark')

```

**Q2:show the country and the area for countries with an area between 200,000 and 250,000.**

```
SELECT name, area FROM world
  WHERE area BETWEEN 200000 AND 250000
  
```

**Q3:Show the countries which have a name that includes the word 'United'**
```
SELECT name
  FROM world
 WHERE name LIKE '%United%'
```

