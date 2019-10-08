# JOIN

### table of game
```
id	mdate	stadium	team1	team2
1001	8 June 2012	National Stadium, Warsaw	POL	GRE
1002	8 June 2012	Stadion Miejski (Wroclaw)	RUS	CZE
1003	12 June 2012	Stadion Miejski (Wroclaw)	GRE	CZE
1004	12 June 2012	National Stadium, Warsaw	POL	RUS
```

### table of goal
```
matchid	teamid	player	gtime
1001	POL	Robert Lewandowski	17
1001	GRE	Dimitris Salpingidis	51
1002	RUS	Alan Dzagoev	15
1002	RUS	Roman Pavlyuchenko	82
```

### table of eteam
```
id	teamname	coach
POL	Poland	Franciszek Smuda
RUS	Russia	Dick Advocaat
CZE	Czech Republic	Michal Bilek
GRE	Greece	Fernando Santos
```

**Q1:List the the dates of the matches and the name of the team in which 'Fernando Santos' was the team1 coach.**
>You can combine the two steps into a single query with a JOIN.
  SELECT *
  FROM game JOIN goal ON (id=matchid)
>To JOIN game with eteam you could use either
game JOIN eteam ON (team1=eteam.id) or game JOIN eteam ON (team2=eteam.id)
```
SELECT game.mdate,eteam.teamname FROM game inner join eteam on eteam.id=game.team1 and eteam.coach='Fernando Santos'
```

### Q2:Instead show the name of all players who scored a goal against Germany.
>You can use teamid!='GER' to prevent listing German players.
>You can use DISTINCT to stop players being listed twice.

```
select DISTINCT(player) 
from goal join game on game.id = goal.matchid and goal.teamid!='GER' and (game.team1='GER' or game.team2='GER')
```



