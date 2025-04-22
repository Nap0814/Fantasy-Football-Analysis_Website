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


# Linear Regression Model for Predicting Next Position Rank

## Model Description
We constructed a linear regression model to predict the **Next_PosRank** (the next position rank) of a player using performance and demographic features. The model was implemented using **scikit-learn's** `Pipeline` and `ColumnTransformer` to facilitate preprocessing and training.

---

## Features Used

The model used the following features:

- **FantPt (Fantasy Points)** — *Quantitative*
- **Age** — *Quantitative*
- **FantPos (Fantasy Position)** — *Nominal*

The **target variable** is **Next_PosRank**, a numeric measure indicating a player's projected future ranking within their position.

---

## Feature Types Summary

| Feature   | Type         | Description                                 |
|-----------|--------------|---------------------------------------------|
| FantPt    | Quantitative | Continuous numerical feature                |
| Age       | Quantitative | Continuous numerical feature                |
| FantPos   | Nominal      | Categorical feature (e.g., QB, RB)          |

- **Quantitative features**: 2  
- **Nominal features**: 1  
- **Ordinal features**: 0

---

## Encoding and Preprocessing

- **Quantitative features** (`FantPt`, `Age`) were passed through without transformation using `"passthrough"`.
- **Nominal feature** (`FantPos`) was encoded using **One-Hot Encoding** via `OneHotEncoder`, with `handle_unknown="ignore"` to avoid errors from unseen categories during testing.
- A `ColumnTransformer` was used to apply these transformations.
- These transformations were combined with a `LinearRegression` model inside a `Pipeline`.

---

## 🧪 Model Evaluation

A **final MAE of 9.60** means that, on average, the model's predicted player ranking is off by about **10 ranks** — a significant improvement from earlier iterations.

- **32.31%** of predictions fall within **±5 ranks**
- **58.60%** of predictions fall within **±10 ranks**
- **80.19%** of predictions fall within **±15 ranks**

### 📊 Positional Accuracy within ±10 Ranks:
- **QB**: 64.75%  
- **WR**: 58.10%  
- **TE**: 56.95%  
- **RB**: 54.79%  
- **FB**: 100.00%
These results indicate that while overall variance explanation is low, the model performs reasonably well for ranking players within a tolerable margin of error—especially for positions like **QB** and **FB**.
