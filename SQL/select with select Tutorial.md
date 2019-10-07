# select with select Tutorial

### The Table of the world

```
name	      continent    area	  population	        gdp
Afghanistan	Asia	      652230	25500100	  20343000000
Albania	    Europe	     28748	 2831741	  12960000000
Algeria	    Africa	   2381741	37100000	 188681000000
Andorra	    Europe	       468	   78115	   3712000000
Angola	    Africa	   1246700	20609294	 100990000000
```

>Find country Bigger than Russia
**Q1:List each country name where the population is larger than that of 'Russia'.**
```
SELECT name FROM world
  WHERE population >
     (SELECT population FROM world
      WHERE name='Russia')
```

>Find Neighbours of Argentina and Australia
**Q2:List the name and continent of countries in the continents containing either Argentina or Australia. Order by name of the country.**
>find the continents where contain either Argentina or Australia,then select the name from that continent.

```
SELECT name, continent
FROM world
WHERE continent IN
    (SELECT continent
     FROM world
     WHERE name IN ('Argentina', 'Australia'))
ORDER BY name
```

**Q3:Germany (population 80 million) has the largest population of the countries in Europe. Austria (population 8.5 million) has 11% of the population of Germany.Show the name and the population of each country in Europe. Show the population as a percentage of the population of Germany.**

>CONCAT(a,b)  →aとbを繋げて「ab」と表示。今回の場合はROUNDした数値に%をつける形。

```
SELECT name, CONCAT(ROUND(population/
    (SELECT population
     FROM world
     WHERE name = 'Germany')
   *100, 0),'%')
FROM world
WHERE continent = 'Europe'
```

**Q4:Which countries have a GDP greater than every country in Europe? [Give the name only.] (Some countries may have NULL gdp values)**
>ALLで特定数値との比較なくすべてを抽出

```
SELECT name
FROM world
WHERE gdp > ALL
    (SELECT gdp
     FROM world
     WHERE continent = 'Europe' AND gdp > 0)
```

### Q5:Find the largest country (by area) in each continent, show the continent, the name and the area:
>inner を探している  ----y.continent=x.continentで両テーブルの一致を探している。
```
SELECT continent, name, area FROM world x
  WHERE area >= ALL
    (SELECT area FROM world y
        WHERE y.continent=x.continent
          AND population>0)
```

### Q6:List each continent and the name of the country that comes first alphabetically.

>文字列カラムに対してmin()を使うと、アルファベット順に最初のもの、となります
```
SELECT continent, min(name)
FROM world
GROUP BY continent
```

### Q7:Some countries have populations more than three times that of any of their neighbours (in the same continent). Give the countries and continents.

```
SELECT name, continent
FROM world x 
WHERE population/3 >= ALL
(SELECT population
FROM world y
WHERE y.continent=x.continent
AND x.name != y.name)
```

