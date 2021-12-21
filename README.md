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