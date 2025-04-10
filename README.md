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



### Pivot tabel
|  | 2TM | 3TM | 4TM | ARI | ATL | BAL | BUF | CAR | CHI | CIN | CLE | DAL | DEN | DET | GNB | HOU | IND | JAX | KAN | LAC | LAR | LVR | MIA | MIN | NOR | NWE | NYG | NYJ | OAK | PHI | PIT | SDG | SEA | SFO | STL | TAM | TEN | WAS |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| FB | 49.0 | 3.0 | 0.0 | 127.0 | 229.0 | 430.0 | 89.0 | 163.0 | 178.0 | 226.0 | 88.0 | 116.0 | 186.0 | 82.0 | 315.0 | 394.0 | 0.0 | 205.0 | 243.0 | 33.0 | 0.0 | 34.0 | 141.0 | 276.0 | 231.0 | 178.0 | 83.0 | 132.0 | 607.0 | 145.0 | 72.0 | 142.0 | 230.0 | 412.0 | 137.0 | 256.0 | 241.0 | 274.0 |
| QB | 941.0 | 0.0 | 0.0 | 4906.0 | 5406.0 | 5366.0 | 5421.0 | 5081.0 | 4616.0 | 5354.0 | 4332.0 | 5590.0 | 5276.0 | 5293.0 | 6328.0 | 5058.0 | 5728.0 | 4904.0 | 5531.0 | 2394.0 | 2208.0 | 1240.0 | 4748.0 | 5080.0 | 5887.0 | 5835.0 | 4810.0 | 4178.0 | 3284.0 | 6261.0 | 5247.0 | 3281.0 | 5634.0 | 4820.0 | 2256.0 | 5362.0 | 4815.0 | 5076.0 |
| RB | 3792.0 | 232.0 | 0.0 | 5349.0 | 6436.0 | 6087.0 | 5792.0 | 5784.0 | 5726.0 | 5424.0 | 5297.0 | 6172.0 | 5884.0 | 6155.0 | 5762.0 | 5733.0 | 6030.0 | 5457.0 | 6514.0 | 2549.0 | 2551.0 | 1396.0 | 5495.0 | 6292.0 | 6919.0 | 6887.0 | 6167.0 | 5591.0 | 4039.0 | 6366.0 | 6055.0 | 4479.0 | 5584.0 | 5503.0 | 3040.0 | 5282.0 | 5959.0 | 5805.0 |
| TE | 611.0 | 2.0 | 0.0 | 1539.0 | 2471.0 | 2900.0 | 1764.0 | 1951.0 | 2057.0 | 1841.0 | 2584.0 | 2808.0 | 2143.0 | 2225.0 | 2248.0 | 2108.0 | 2938.0 | 1880.0 | 3205.0 | 956.0 | 876.0 | 709.0 | 2372.0 | 2158.0 | 3446.0 | 3184.0 | 2229.0 | 1655.0 | 1569.0 | 2823.0 | 2120.0 | 2071.0 | 2255.0 | 2561.0 | 922.0 | 2435.0 | 2478.0 | 2572.0 |
| WR | 4497.0 | 225.0 | -1.0 | 7901.0 | 7137.0 | 6077.0 | 6697.0 | 6552.0 | 6194.0 | 8308.0 | 5782.0 | 8051.0 | 7544.0 | 7617.0 | 9029.0 | 7108.0 | 7686.0 | 6858.0 | 6247.0 | 3135.0 | 3802.0 | 1724.0 | 6872.0 | 7457.0 | 7926.0 | 6957.0 | 7181.0 | 6295.0 | 4745.0 | 7227.0 | 8123.0 | 4096.0 | 7670.0 | 6281.0 | 3848.0 | 7776.0 | 6181.0 | 6535.0 |

