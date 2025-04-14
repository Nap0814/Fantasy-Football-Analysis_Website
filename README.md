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

<table border="1" class="dataframe">
    <thead>
      <tr style="text-align: right;">
        <th>Tm</th>
        <th>2TM</th>
        <th>3TM</th>
        <th>4TM</th>
        <th>ARI</th>
        <th>ATL</th>
        <th>BAL</th>
        <th>BUF</th>
        <th>CAR</th>
        <th>CHI</th>
        <th>CIN</th>
        <th>CLE</th>
        <th>DAL</th>
        <th>DEN</th>
        <th>DET</th>
        <th>GNB</th>
        <th>HOU</th>
        <th>IND</th>
        <th>JAX</th>
        <th>KAN</th>
        <th>LAC</th>
        <th>LAR</th>
        <th>LVR</th>
        <th>MIA</th>
        <th>MIN</th>
        <th>NOR</th>
        <th>NWE</th>
        <th>NYG</th>
        <th>NYJ</th>
        <th>OAK</th>
        <th>PHI</th>
        <th>PIT</th>
        <th>SDG</th>
        <th>SEA</th>
        <th>SFO</th>
        <th>STL</th>
        <th>TAM</th>
        <th>TEN</th>
        <th>WAS</th>
      </tr>
      <tr>
        <th>FantPos</th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <th>FB</th>
        <td>49.0</td>
        <td>3.0</td>
        <td>0.0</td>
        <td>127.0</td>
        <td>229.0</td>
        <td>430.0</td>
        <td>89.0</td>
        <td>163.0</td>
        <td>178.0</td>
        <td>226.0</td>
        <td>88.0</td>
        <td>116.0</td>
        <td>186.0</td>
        <td>82.0</td>
        <td>315.0</td>
        <td>394.0</td>
        <td>0.0</td>
        <td>205.0</td>
        <td>243.0</td>
        <td>33.0</td>
        <td>0.0</td>
        <td>34.0</td>
        <td>141.0</td>
        <td>276.0</td>
        <td>231.0</td>
        <td>178.0</td>
        <td>83.0</td>
        <td>132.0</td>
        <td>607.0</td>
        <td>145.0</td>
        <td>72.0</td>
        <td>142.0</td>
        <td>230.0</td>
        <td>412.0</td>
        <td>137.0</td>
        <td>256.0</td>
        <td>241.0</td>
        <td>274.0</td>
      </tr>
      <tr>
        <th>QB</th>
        <td>941.0</td>
        <td>0.0</td>
        <td>0.0</td>
        <td>4906.0</td>
        <td>5406.0</td>
        <td>5366.0</td>
        <td>5421.0</td>
        <td>5081.0</td>
        <td>4616.0</td>
        <td>5354.0</td>
        <td>4332.0</td>
        <td>5590.0</td>
        <td>5276.0</td>
        <td>5293.0</td>
        <td>6328.0</td>
        <td>5058.0</td>
        <td>5728.0</td>
        <td>4904.0</td>
        <td>5531.0</td>
        <td>2394.0</td>
        <td>2208.0</td>
        <td>1240.0</td>
        <td>4748.0</td>
        <td>5080.0</td>
        <td>5887.0</td>
        <td>5835.0</td>
        <td>4810.0</td>
        <td>4178.0</td>
        <td>3284.0</td>
        <td>6261.0</td>
        <td>5247.0</td>
        <td>3281.0</td>
        <td>5634.0</td>
        <td>4820.0</td>
        <td>2256.0</td>
        <td>5362.0</td>
        <td>4815.0</td>
        <td>5076.0</td>
      </tr>
      <tr>
        <th>RB</th>
        <td>3792.0</td>
        <td>232.0</td>
        <td>0.0</td>
        <td>5349.0</td>
        <td>6436.0</td>
        <td>6087.0</td>
        <td>5792.0</td>
        <td>5784.0</td>
        <td>5726.0</td>
        <td>5424.0</td>
        <td>5297.0</td>
        <td>6172.0</td>
        <td>5884.0</td>
        <td>6155.0</td>
        <td>5762.0</td>
        <td>5733.0</td>
        <td>6030.0</td>
        <td>5457.0</td>
        <td>6514.0</td>
        <td>2549.0</td>
        <td>2551.0</td>
        <td>1396.0</td>
        <td>5495.0</td>
        <td>6292.0</td>
        <td>6919.0</td>
        <td>6887.0</td>
        <td>6167.0</td>
        <td>5591.0</td>
        <td>4039.0</td>
        <td>6366.0</td>
        <td>6055.0</td>
        <td>4479.0</td>
        <td>5584.0</td>
        <td>5503.0</td>
        <td>3040.0</td>
        <td>5282.0</td>
        <td>5959.0</td>
        <td>5805.0</td>
      </tr>
      <tr>
        <th>TE</th>
        <td>611.0</td>
        <td>2.0</td>
        <td>0.0</td>
        <td>1539.0</td>
        <td>2471.0</td>
        <td>2900.0</td>
        <td>1764.0</td>
        <td>1951.0</td>
        <td>2057.0</td>
        <td>1841.0</td>
        <td>2584.0</td>
        <td>2808.0</td>
        <td>2143.0</td>
        <td>2225.0</td>
        <td>2248.0</td>
        <td>2108.0</td>
        <td>2938.0</td>
        <td>1880.0</td>
        <td>3205.0</td>
        <td>956.0</td>
        <td>876.0</td>
        <td>709.0</td>
        <td>2372.0</td>
        <td>2158.0</td>
        <td>3446.0</td>
        <td>3184.0</td>
        <td>2229.0</td>
        <td>1655.0</td>
        <td>1569.0</td>
        <td>2823.0</td>
        <td>2120.0</td>
        <td>2071.0</td>
        <td>2255.0</td>
        <td>2561.0</td>
        <td>922.0</td>
        <td>2435.0</td>
        <td>2478.0</td>
        <td>2572.0</td>
      </tr>
      <tr>
        <th>WR</th>
        <td>4497.0</td>
        <td>225.0</td>
        <td>-1.0</td>
        <td>7901.0</td>
        <td>7137.0</td>
        <td>6077.0</td>
        <td>6697.0</td>
        <td>6552.0</td>
        <td>6194.0</td>
        <td>8308.0</td>
        <td>5782.0</td>
        <td>8051.0</td>
        <td>7544.0</td>
        <td>7617.0</td>
        <td>9029.0</td>
        <td>7108.0</td>
        <td>7686.0</td>
        <td>6858.0</td>
        <td>6247.0</td>
        <td>3135.0</td>
        <td>3802.0</td>
        <td>1724.0</td>
        <td>6872.0</td>
        <td>7457.0</td>
        <td>7926.0</td>
        <td>6957.0</td>
        <td>7181.0</td>
        <td>6295.0</td>
        <td>4745.0</td>
        <td>7227.0</td>
        <td>8123.0</td>
        <td>4096.0</td>
        <td>7670.0</td>
        <td>6281.0</td>
        <td>3848.0</td>
        <td>7776.0</td>
        <td>6181.0</td>
        <td>6535.0</td>
      </tr>
    </tbody>
  </table>
  


