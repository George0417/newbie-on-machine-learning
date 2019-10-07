# select from nobel tutorial

### The Table of Nobel 
    yr	subject	  winner
    
   1960	Chemistry	Willard F. Libby
   
   1960	Medicine	Sir Frank Macfarlane Burnet
   
   1960	Medicine	Peter Madawar
   
   ...
   
**Q1:Show all details (yr, subject, winner) of the Literature prize winners for 1980 to 1989 inclusive.**
>select * means select all elements from the table

```
SELECT *
FROM nobel
WHERE subject = 'Literature'
  AND yr BETWEEN 1980 and 1989

```

**Q2:Show year, subject, and name of people who won a 'Medicine' prize in an early year (before 1910, not including 1910) 
together with winners of a 'Literature' prize in a later year (after 2004, including 2004)**

```
SELECT * 
FROM nobel
WHERE (yr < 1910 and subject = 'Medicine')
  OR (yr >= 2004 and subject = 'Literature')
 ```

**Q3:Find all details of the prize won by EUGENE O'NEILL**
>文字列内の「'」（シングルクオーテーション）は２個続けて書けばいいよ、ということ。
 ```
SELECT *
FROM nobel
WHERE winner = 'EUGENE O''NEILL'
 ```
 
**Q4:List the winners, year and subject where the winner starts with Sir. Show the the most recent first, then by name order.** 
```
SELECT winner, yr, subject
FROM nobel
WHERE winner LIKE 'Sir%'
  ORDER BY yr, winner
```
 
### Q5:The expression subject IN ('Chemistry','Physics') can be used as a value (it will be 0 or 1.)
Show the 1984 winners and subject ordered by subject and winner name; but list Chemistry and Physics last.

>「INに含まれるものに1を、それ以外には0を付与される」ことを利用し、それ順に並べるということをしています。

```
SELECT winner, subject
  FROM nobel
 WHERE yr=1984
 ORDER BY subject IN ('Physics','Chemistry'), subject, winner
```
 
 


