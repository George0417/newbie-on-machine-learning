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

**Q4:Show the countries that are big by area or big by population but not both. Show name, population and area.**
>One or the other (but not both)

```
SELECT name, population, area
FROM world
WHERE area >= 3000000 xor population >= 250000000
```

**Q5:For South America show population in millions and GDP in billions both to 2 decimal places.**
>ROUND(数値, n)で小数点以下n桁に丸めます（四捨五入）。nは有効桁数と呼び、0が1の位、1が小数点以下第一位、-1が10の位です。

```
SELECT name, ROUND(population/1000000, 2), ROUND(gdp/1000000000, 2)
FROM world
WHERE continent = 'South America'
```
>ROUND(gdp/population, -3) means 1000以上


**Q6:Name and capital have the same length**
```
SELECT name, capital
  FROM world
 WHERE LENGTH(name) = LENGTH(capital)

```
### Q7:Show the name and the capital where the first letters of each match. Don't include countries where the name and the capital are the same word.
```
SELECT name,capital
  FROM world
 WHERE LEFT(name,1) = LEFT(capital,1) and name <> capital
```

**Q8: the vowels have(a e i o u) in the name. 
Find the country that has all the vowels and no spaces in its name.**
```
SELECT name
  FROM world
 WHERE name LIKE '%a%' 
  and name LIKE '%i%' 
　and name LIKE '%u%'
  and name LIKE '%e%'
  and name LIKE '%o%'
   AND name NOT LIKE '% %'
```

