# NBA_Rookie_Analysis
## Introduction & Data Description.
NBA is a competitive sports league that each team should spend lots of resource to form a team. During off-season, every team is busy making plan on how to be a competitive team in next season. They should decide who they should keep, who should be traded, and who has the talent and worth investing. What’s more, rookies are hard to judge their development in the future only based on the first-year performance. 

In this project, I plan to Analyze [NBA rookie's statistic data](https://www.kaggle.com/sveneschlbeck/nba-players-career-duration) from Kaggle to find out the pattern of successful players and try to predict if a player can stay more than five years in NBA. The average career duration of players is 4.6 years so five years is already an above average player. I hope the analysis and predictive model can help on deciding if a team should invest more resources on rookies to help them grow up and explore talented players.

The dataset is in csv file and there are 21 columns which the first column is the name of the player and the last is the target: if a player plays over five years, a binary variable (1 means over five year and 0 otherwise). For the target, there are 825 players played over 5 years (62%) and 503 players did not (38%), so the data is a little imbalanced but not serious. Also, there are 19 features such as the number of games played, points per game and other statistic in first season can be used to predict the target.

## Analysis
To understand the dataset and target better, I use logistic regression to see which features are important indicator to player who can play over 5 years. The most one is game played followed by offensive rebound. The distributions of these features (figure 1, 2) also show the difference between two classes. The players who play over five years do play more games with more offensive rebound in their rookie year. 

Last, plotting the correlation matrix (figure 3) to see the relation between features. According to the graph, some features are highly correlated such as points per game and field goals made, points per game and field goal attempts, etc. These is a point I should concern.

| ![figure1](https://github.com/peterhuang024/NBA_Rookie_Analysis/blob/master/Graph/figure_1.png) | ![figure2](https://github.com/peterhuang024/NBA_Rookie_Analysis/blob/master/Graph/figure_2.png) 
|:--:|:--:|
| Figure 1: Distribution of game played of players play over five years or not | Figure 2: Distribution of offensive rebounds of players play over five years or not |

| ![figure3](https://github.com/peterhuang024/NBA_Rookie_Analysis/blob/master/Graph/figure_3.png) |
|:--:|
| Figure 3: Pairwise correlation of all 19 features. Both axes are 19 features.|

## Data Preprocessing
First, the original data has 1,340 data points but there is duplication. After removing duplications, there are 1,328 distinct rows remaining. Next, there is no null value and all features are float or integer type in the dataset. Then, separated into 80% training data and 20% testing data. In this analysis, I used the training data to do the parameter tuning and testing data to check each model’s performance. I also tried some feature engineering such as PCA and scaled features; however, the performance does not improve. Thus, in this analysis, I only report the result using original attributes.

## Classification Models & Result
This task used 3 tree-based algorithms: Decision Tree, Random Forests, and Gradient Boosting Trees. For parameter-tuning, applying grid search with 5 folds cross validation and accuracy as evaluation to train 3 models and get the best parameters. Model results are summarized in below table. In addition, trained a random forest with scaled features to compare feature importance. Importance bar charts and features distribution in figure 4, 5, 6, 7. (More model and evaluation detail such as AUC graphs and model training can refer the notebook)

| Metrics\Algorithms | Decision Tree | Random Forest | Gradient Boosting |
| ----------- | ----------- | ----------- | ----------- |
| Precision | 0.78 | 0.81 | 0.80 |
| Recall | 0.79 | 0.80 | 0.84 |
| F1-score | 0.79 | 0.80 | 0.81 |
| Accuracy | 71% | 74% | 74% |
| AUC | 0.73 | 0.78 | 0.78 |

| ![figure4](https://github.com/peterhuang024/NBA_Rookie_Analysis/blob/master/Graph/figure_4.png) | ![figure5](https://github.com/peterhuang024/NBA_Rookie_Analysis/blob/master/Graph/figure_5.png) 
|:--:|:--:|
| Figure 4: Feature importance from random forest. The top 5 features are game played, field goal made, points per game, field goal percentage, and minutes played. | Figure 5: Distribution of field goals made of players play over five years or not |
| ![figure6](https://github.com/peterhuang024/NBA_Rookie_Analysis/blob/master/Graph/figure_6.png) | ![figure7](https://github.com/peterhuang024/NBA_Rookie_Analysis/blob/master/Graph/figure_7.png) 
| Figure 6: Distribution of average points per game of players play over five years or not. The red line is the average of rookie of the year in the past 25 seasons. | Figure 7: Distribution of average field goal percentage of players play over five years or not. The red line is the average of rookie of the year in the past 25 seasons. |

## Reference
- [NBA players career duration dataset](https://www.kaggle.com/sveneschlbeck/nba-players-career-duration)
- [Scikit-Learn for machine learning](https://scikit-learn.org/stable/)
- [NBA career length information](https://dunkorthree.com/nba-player-career-length/)
- [Rookie of the year data](http://www.espn.com/nba/history/awards/_/id/35)