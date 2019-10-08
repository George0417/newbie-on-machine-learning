# SUM and COUNT

### Table of world
```
name	continent	area	population	gdp
Afghanistan	Asia	652230	25500100	20343000000
Albania	Europe	28748	2831741	12960000000
Algeria	Africa	2381741	37100000	188681000000
Andorra	Europe	468	78115	3712000000
Angola	Africa	1246700	20609294	100990000000

```

**Q1:List all the continents - just once each.**
```
SELECT DISTINCT continent 
FROM world
```

**Q2:What is the total population of ('Estonia', 'Latvia', 'Lithuania')**
```
Select sum(population)
from world 
where name in ('Estonia', 'Latvia', 'Lithuania')

```

**Q3:For each continent show the continent and number of countries.**
>continentごとに集計する、という指定のために「GROUP BY」が必要です。
```
SELECT continent, COUNT(name)
FROM world
GROUP BY continent
```

**Q4:List the continents that have a total population of at least 100 million.**
>HAVING句は集計した後の結果で結果が絞られます。
WHERE句は集計する前の値で結果を絞るので、この場合は不適当。
書く順序に違和感があるかも知れませんが、GROUP BY句のあとにHAVING句が読み込まれます。
```
SELECT continent
FROM world
GROUP BY continent
 HAVING SUM(population) >= 100000000

```
