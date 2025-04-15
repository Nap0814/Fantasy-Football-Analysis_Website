## Introduction and Question Identification  
#### We’re using a dataset combining stats from Pro Football Reference and PFF, which includes ~12,000 player-season entries and around 25 features. It covers standard NFL stats (like targets, carries, and touchdowns), fantasy metrics (like points per game and rank), and advanced features like player grades and red zone usage.
## Main Question  
#### Can we predict a player's final fantasy football rank for the next season using prior-year stats and player grades?
This matters because millions play fantasy football, and being able to spot breakout players or avoid busts can give players a huge edge.
## Key Columns
FantPos: Player’s fantasy position (RB, WR, etc.)
Age: Age of the player during the season
Tgt, Rec, Yds, TD: Receiving stats
Att, Yds, TD: Rushing stats
FantPt, PPR: Total and PPR fantasy points scored
PosRank, OvRank: Player’s position and overall fantasy ranking (target)


### All Da plots 

# Univariate
## Pie chart
 <iframe
 src="assets/PositionPieChart.html"
 width="800"
 height="600"
 frameborder="0"
 ></iframe>
 This pie chart shows the distibution of fantasy positions available in out dataset. Based on this chart we can see that there are more Fanstasy recivers than any other position.

# Multivariate
## Points vs Position BoxPlot
 <iframe
 src="assets/PointsvsPositionBoxPlot.html"
 width="800"
 height="600"
 frameborder="0"
 ></iframe>
 This box plot shows the distribution of points by position. This Plot shows us that the most valuble position is quarterback followed by runningback. 

 ## Fantasy Points Vs Year Histogram
 <iframe
 src="assets/FantasyPointsVsYearHistogram.html"
 width="800"
 height="600"
 frameborder="0"
 ></iframe>
 This Histogram shows how the number of fanstasy points scored changed thoughout the years. We can see from this that as time goes on the points scored seems to increace.  



### Pivot table

<iframe
 src="assets/Heat_Map_Pivot_Table.html"
 width="800"
 height="600"
 frameborder="0"
 ></iframe>

 This heat map shows the top 10 teams that output the most Fantasy points. With this we can see the cerain positions perform better on certain teams.
