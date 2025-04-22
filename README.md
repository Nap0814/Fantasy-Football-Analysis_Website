# Dataset Introduction and Question Identification

## Data Overview  

We’re using a dataset from [Pro Football Reference](https://www.pro-football-reference.com/years/2024/fantasy.htm), which includes ~12,000 player-season entries and around 35 features. It covers standard NFL stats (like targets, carries, and touchdowns), fantasy metrics (like points per game and rank), and advanced features like player grades and red zone usage over since 2004.  

## Main Question  
#### Can we predict a player's final fantasy football rank for the next season using prior-year stats and player grades?
This matters because millions play fantasy football, and being able to spot breakout players or avoid busts can give players a huge edge.
## Key Columns
`FantPos`: Player’s fantasy position (RB, WR, etc.)  
`Age`: Age of the player during the season  
`Tgt`: Rec, Yds, TD: Receiving stats  
`Att`: Yds, TD: Rushing stats  
`FantPt`: PPR: Total and PPR fantasy points scored  
`PosRank`: OvRank: Player’s position and overall fantasy ranking (target)  


# Data Cleaning and Exploratory Data Analysis

## Data Cleaning

To prepare the dataset for analysis, we first addressed symbolic annotations in player names—specifically asterisks (`*`) indicating Pro Bowl selections and plus signs (`+`) indicating All-Pro honors. These symbols were part of the original data collection process from Pro Football Reference, where such accolades are embedded directly into player names. To reflect this, we extracted them into two binary columns (`is_probowl` and `is_allpro`) and cleaned the `Player` column to ensure consistent, identifier-friendly names for joins and tracking.

Ambiguous columns like `Yds`, `Yds.1`, and `TD.1` stemmed from the original website’s formatting for multiple stat types (e.g., passing, rushing), so we renamed them to `Pass_yd`, `Rush_yd`, and `Rush_TD` for clarity and usability in downstream analysis.

Team abbreviations were standardized (e.g., `SDG` to `LAC`, `STL` to `LAR`) to align with current franchise naming conventions, accounting for relocations that would otherwise fragment team-based aggregations.

Most missing statistics were filled with zeros, assuming these reflected zero performance rather than true missing data, as the original site omits stats when no play occurred. For example, the `2PM` column was often NaN, since many times players don't record this stat. For the `OvRank` column we imputed the maximum value for that given year, since all values that were NaN in this column fell below a baseline rank set by Pro Football Reference. We used the maximum value since we deemed players below the the threshold to be equal in rank.

Finally, we created a `Next_PosRank` column by applying a group-wise shift based on player and position—mirroring the year-to-year progression of the NFL season—to support predictive modeling of future fantasy performance.

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Rk</th>
      <th>Player</th>
      <th>Tm</th>
      <th>FantPos</th>
      <th>Age</th>
      <th>G</th>
      <th>GS</th>
      <th>Cmp</th>
      <th>Att</th>
      <th>Pass_yd</th>
      <th>Pass_TD</th>
      <th>Int</th>
      <th>Rush_Att</th>
      <th>Rush_yd</th>
      <th>Y/A</th>
      <th>Rush_TD</th>
      <th>Tgt</th>
      <th>Rec</th>
      <th>Rec_yd</th>
      <th>Y/R</th>
      <th>Rec_TD</th>
      <th>Fmb</th>
      <th>FL</th>
      <th>TD.3</th>
      <th>2PM</th>
      <th>2PP</th>
      <th>FantPt</th>
      <th>PPR</th>
      <th>DKPt</th>
      <th>FDPt</th>
      <th>VBD</th>
      <th>PosRank</th>
      <th>OvRank</th>
      <th>-9999</th>
      <th>Year</th>
      <th>is_probowl</th>
      <th>is_allpro</th>
      <th>Next_PosRank</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3804</th>
      <td>34</td>
      <td>A.J. Brown</td>
      <td>TEN</td>
      <td>WR</td>
      <td>22</td>
      <td>16</td>
      <td>11.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>60.0</td>
      <td>20.0</td>
      <td>1.0</td>
      <td>84.0</td>
      <td>52.0</td>
      <td>1051.0</td>
      <td>20.21</td>
      <td>8.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>9</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>165.0</td>
      <td>217.1</td>
      <td>220.1</td>
      <td>191.1</td>
      <td>36.0</td>
      <td>9</td>
      <td>34.0</td>
      <td>BrowAJ00</td>
      <td>2019</td>
      <td>0</td>
      <td>0</td>
      <td>9.0</td>
    </tr>
    <tr>
      <th>601</th>
      <td>29</td>
      <td>A.J. Brown</td>
      <td>TEN</td>
      <td>WR</td>
      <td>23</td>
      <td>14</td>
      <td>12.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>106.0</td>
      <td>70.0</td>
      <td>1075.0</td>
      <td>15.36</td>
      <td>11.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>12</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>178.0</td>
      <td>247.5</td>
      <td>251.5</td>
      <td>212.5</td>
      <td>51.0</td>
      <td>9</td>
      <td>29.0</td>
      <td>BrowAJ00</td>
      <td>2020</td>
      <td>1</td>
      <td>0</td>
      <td>32.0</td>
    </tr>
    <tr>
      <th>1331</th>
      <td>102</td>
      <td>A.J. Brown</td>
      <td>TEN</td>
      <td>WR</td>
      <td>24</td>
      <td>13</td>
      <td>13.0</td>
      <td>0.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2.0</td>
      <td>10.0</td>
      <td>5.0</td>
      <td>0.0</td>
      <td>105.0</td>
      <td>63.0</td>
      <td>869.0</td>
      <td>13.79</td>
      <td>5.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>5</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>118.0</td>
      <td>180.9</td>
      <td>183.9</td>
      <td>149.4</td>
      <td>0.0</td>
      <td>32</td>
      <td>0.0</td>
      <td>BrowAJ00</td>
      <td>2021</td>
      <td>0</td>
      <td>0</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>3134</th>
      <td>13</td>
      <td>A.J. Brown</td>
      <td>PHI</td>
      <td>WR</td>
      <td>25</td>
      <td>17</td>
      <td>16.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>145.0</td>
      <td>88.0</td>
      <td>1496.0</td>
      <td>17.00</td>
      <td>11.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>11</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>212.0</td>
      <td>299.6</td>
      <td>304.6</td>
      <td>255.6</td>
      <td>91.0</td>
      <td>4</td>
      <td>13.0</td>
      <td>BrowAJ00</td>
      <td>2022</td>
      <td>1</td>
      <td>0</td>
      <td>8.0</td>
    </tr>
    <tr>
      <th>2509</th>
      <td>20</td>
      <td>A.J. Brown</td>
      <td>PHI</td>
      <td>WR</td>
      <td>26</td>
      <td>17</td>
      <td>17.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>158.0</td>
      <td>106.0</td>
      <td>1456.0</td>
      <td>13.74</td>
      <td>7.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>7</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>184.0</td>
      <td>289.6</td>
      <td>294.6</td>
      <td>236.6</td>
      <td>51.0</td>
      <td>8</td>
      <td>20.0</td>
      <td>BrowAJ00</td>
      <td>2023</td>
      <td>1</td>
      <td>0</td>
      <td>17.0</td>
    </tr>
  </tbody>
</table>



# Univariate Analysis
## Pie chart of Position distribution
 <iframe
 src="assets/PositionPieChart.html"
 width="800"
 height="600"
 frameborder="0"
 ></iframe>
 This pie chart displays the distribution of fantasy football positions in our dataset, with wide receivers making up the largest group. This suggests that WRs are the most common fantasy players, which could influence drafting depth and positional strategies.

# Bivariate Analysis
## Points vs Position BoxPlot
 <iframe
 src="assets/PointsvsPositionBoxPlot.html"
 width="800"
 height="600"
 frameborder="0"
 ></iframe>
 This box plot shows the distribution of fantasy points by position, with quarterbacks having the highest median point totals. This suggests that quarterbacks are generally the most valuable fantasy players, followed by running backs. 
 

 ## Fantasy Points Vs Year Histogram
 
 <iframe
 src="assets/FantasyPointsVsYearHistogram.html"
 width="800"
 height="600"
 frameborder="0"
 ></iframe>
 his histogram shows how the number of fantasy points scored has changed over the years. It reveals an upward trend, indicating that players have been scoring more fantasy points in recent seasons. 



### Heat Map of Score output per team

<iframe
 src="assets/Heat_Map_Pivot_Table.html"
 width="800"
 height="600"
 frameborder="0"
 ></iframe>

 This heatmap highlights how the top 10 NFL teams distribute Fantasy Points across positions, revealing which teams are especially strong at specific roles like QB, RB, TE, or WR. It helps identify team-position combinations that consistently produce high fantasy value.

# Step 3: The Prediction Problem

## Prediction Problem

Our goal is to build a **regression model** that predicts an NFL player's final fantasy position ranking for the upcoming season, using their performance statistics from the previous season.

---

## Response Variable

**Next PosRank** (next season’s fantasy ranking within position) is the response variable we aim to predict.

We chose **Next PosRank** because it offers a normalized, position-specific measure of a player’s fantasy value. This makes it especially useful for fantasy football managers when planning draft strategies or identifying breakout candidates within specific roles (e.g., WR, RB, QB).

---

## Type of Prediction

This is a **regression** problem.  
Although ranks are ordinal, we treat them as continuous for prediction purposes, since we aim to estimate the **exact** or **near-exact** rank value rather than classify into broad tiers.

We also measure performance not just by exact rank, but how close the prediction is to the actual outcome.

---

## Evaluation Metric

We use **Mean Absolute Error (MAE)** as our primary evaluation metric.

We chose MAE because:

- It is directly interpretable in the same units as our target variable (ranking position), making it easy to explain and understand.
- Unlike R² or RMSE, MAE is more robust to outliers and gives a straightforward sense of how far off predictions are on average.
- It aligns well with how fantasy managers might perceive draft accuracy (e.g., off by 2–3 ranks is more intuitive than a % variance).

---


# Baseline Model Predicting Next Position Rank

## Model Description
We constructed a regression model to predict the `Next_PosRank` (the next position rank) of a player using FantPt and Age.

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

## Model Evaluation

A **final MAE of 9.60** means that, on average, the model's predicted player ranking is off by about **10 ranks** — a significant improvement from earlier iterations.

- **32.31%** of predictions fall within ** 5 ranks**
- **58.60%** of predictions fall within ** 10 ranks**
- **80.19%** of predictions fall within ** 15 ranks**

### Positional Accuracy within ±10 Ranks:
- **QB**: 64.75%  
- **WR**: 58.10%  
- **TE**: 56.95%  
- **RB**: 54.79%  
- **FB**: 100.00%




# Final Model  

### Feature Engineering  

To better capture the underlying patterns in the data and enhance the model's ability to predict player ranks, we introduced several new features:

- **Total_TD**: Total Touchdown summing from each category, rushing, passing etc.
- **Touches**: Combines rushing attempts and receptions which are crucial for fantasy production.
- **YardsPerTouch**: Measures efficiency per opportunity. High efficiency often correlates with better fantasy output and can help differentiate players with similar usage levels.
- **CatchRate**: Reflects how often a player successfully catches a target. Particularly useful for receivers and tight ends.
- **TD_PG, RecYards_PG, RushYards_PG**: Normalizing stats per game accounts for variability in games played, which is especially important due to injuries or mid-season trades.
- **FantPt_PerTouch**: Measures fantasy productivity per opportunity, which helps adjust for volume vs. efficiency.
- **TeamYearRank**: Ranks a player's fantasy points within their team and season, contextualizing individual performance relative to team role and system.

These engineered features were designed based on football logic and performance analytics rather than arbitrary selection or outcome-based tuning, making them strong candidates for improving generalization.

---

### Modeling Algorithm and Hyperparameter Selection

I used the `LogisticAT` (ordinal regression with an adjacent-category logistic model) as the core modeling algorithm. This was selected because our target is **ordinal**—a ranking where the order matters, but the distance between ranks is not consistent or known. `LogisticAT` is specifically designed for such tasks, making it more appropriate than standard regression or classification models.

To find the optimal hyperparameter (`alpha`), I used **cross-validation** on the training set and selected the value that minimized the Mean Absolute Error (MAE) on validation folds. The best performing `alpha` was **100.0**, which likely provided the right balance between model complexity and regularization.

---

### Final Model vs. Baseline Model

| Metric                 | Baseline Model | Final Model | Improvement   |
|------------------------|----------------|-------------|---------------|
| MAE                    | 9.85           | 9.36        |   Lower error |
| Accuracy Score         | 0.02           | 0.04        |   Improved    |
| Accuracy ±5 ranks      | 33.12%         | 35.39%      |   Higher      |
| Accuracy ±10 ranks     | 58.77%         | 60.23%      |   Higher      |
| Accuracy ±15 ranks     | 78.25%         | 82.31%      |   Higher      |

The final model demonstrated consistent improvements across all key metrics. While the raw accuracy score remains low due to the challenging nature of rank prediction, the model substantially improved on meaningful ordinal metrics like accuracy within ±10 and ±15 ranks. Notably, accuracy within ±10 ranks increased across most positions, with significant jumps for **QB** and **FB**, where contextual features like per-game efficiency and role-adjusted ranking were particularly impactful.

