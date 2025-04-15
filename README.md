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
 This box plot shows the distribution of points by position. This Plot shows us that the most valuable position is quarterback followed by runningback. 

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

 This heat map shows the top 10 teams that output the most Fantasy points. With this, we can see that certain positions perform better on certain teams.

# Step 3: The Prediction Problem

### ✅ Prediction Problem

We aim to build a regression model to predict a player's final fantasy ranking for the next NFL season based on their previous season's performance statistics.

### 🎯 Response Variable

Our response variable is OvRank — the player's overall fantasy ranking at the end of the following season.

We chose OvRank because it represents a comprehensive, standardized measure of a player's fantasy value across all positions. It's especially useful in helping fantasy managers plan their draft strategies or identify breakout candidates.

### 📊 Type of Prediction

This is a regression problem (not classification), since OvRank is a continuous and ordinal numeric value. Predicting the actual rank (e.g., RB #4, WR #15 overall, etc.) allows for more nuance than bucketing players into performance tiers.

### 📈 Evaluation Metric

We will evaluate our model using Mean Absolute Error (MAE).

We chose MAE because:

1) It is interpretable in the same units as the response variable (ranking position).
2) It treats all errors linearly and doesn't over-penalize large outliers like RMSE does.
3) It is more intuitive than metrics like R² when comparing real vs. predicted ranks.

