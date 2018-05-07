## PHBS_TQFML - Final Project - Yipang Lin

# Topics
"What kind of player will be voted as the MVP in NBA this season?"

## Motivation
1. a big fan of NBA
2. Basketball players across different positions can be measured using the same set of statistics, but like volleyball is very hard.

## What is MVP
The National Basketball Association (NBA) Most Valuable Player Award (MVP) is an annual National Basketball Association (NBA) award given to the best performing player of the regular season.

## How to choose MVP - Voting and voting system
By voting!
Since the 1980–81 season, the award is decided by a panel of sportswriters and broadcasters throughout the United States and Canada.
Each member of the voting panel casts a vote for first to fifth place selections. Each first-place vote is worth 10 points; each second-place vote is worth seven; each third-place vote is worth five, fourth-place is worth three and fifth-place is worth one.

## Voting based on...
Steve Aschburner: "The MVP is the best player on the team with the best record."
Fran Blinebury: "Consistent individual excellence combined with team leadership and more than a few moments of transcendent brilliance."
John Schuhmann: "My vote went to the individual who had the biggest effect on why a good team was good."
Ian Thomsen: "I love this award because it’s all about value: who has done the most for his team?"

We can know that the media vote the MVP based on the contribution of the player to the team, which can be observed from personal statistics and team winning percentage (team standing).

## Project Goal
To predict MVP candidates or even MVP in 2016-2017 season by training model using classfication from MVP + MVP candidates and other players .

## Data
What kind of data do we need?
  1. Individual Stats (with Past MVP winners records) (@Seasons_Stats.csv)
  2. Team Stats (@nbastandings.csv)
-Data are from basketball-reference.com and Kaggle dataset "NBA Players stats since 1950", with stats for all players since 1950. 
  
## Features:

@Seasons_Stats.csv
1. Games played (G) - How many games did the player play that season.
2. Minutes played (MP) - How many minutes did the player play that season.
3. Field goal percentage (FG%) - The ratio of field goals made to field goals attempted.
4. 3-Point Field Goal Percentage (3P%) -  The ratio of field goals made from 3-Pt line to field goals from 3-Pt line attempted.
5. True Shooting Percentage (TS%) - A measure of shooting efficiency that takes into account 2-point field goals, 3-point field goals, and free throws.
6. Player Efficiency Rank (PER) – A measure of per-minute production standardized such that the league average is 15.
7. Assist Percentage (AST%) - An estimate of the percentage of teammate field goals a player assisted while he was on the floor.
8. Steal Percentage (STL%) - An estimate of the percentage of opponent possessions that end with a steal by the player while he was on the floor.
9. Total Rebounds percentage (TRB%) - An estimate of the percentage of available rebounds a player grabbed while he was on the floor.
10. Blocks Percentage (BLK%) - An estimate of the percentage of opponent two-point field goal attempts blocked by the player while he was on the floor.
11. Turnover Percentage (TOV%) - An estimate of turnovers committed per 100 plays.
12. Win Shares (WS) – Estimated number of wins created by the player
13. Box Plus/Minus (BPM) - A box score estimate of the points per 100 possessions a player contributed above a league-average player, translated to an average team.
14. Value over Replacement Player (VORP) - A box score estimate of the points per 100 TEAM possessions that a player contributed above a replacement-level (-2.0) player, translated to an average team and prorated to an 82-game season.
15. Usage Percentage (USG%) - An estimate of the percentage of team plays used by a player while he was on the floor.
16. Points won (Pts Won) - The total voting points won by the player.
17. Points max (Pts Max) - The max voting points each player can get at that season.
18. MVP - If the player was the candidate of MVP at that year.
19. VoteShare - Vote Point / Total Point

@nbastandings.csv
1. Numbers of winning games (W)
2. Numbers of losing games (L)
==> combine them to winning rate (W/L%).


## Methods
- Try DecisionTree/RandomForest/LinearSVC/Synthetic Minority Oversampling Technique (SMOTE)/Bagging method to classify between MVP player and normal player.
- use different VoteShare rate as standards to redo the predict of MVP.
- If the required VoteShare is high enough then the predicted value should be the MVP of that season.

## Procedure
1. Data Choosing & Cleaning
  -Data from 1980-1981 season to 2016-2017 season, because nowadays voting system was established at 1980-1981 season.
  -Use the highest ten vote-points candidates vs. other players to classify data.
  -Keep only players with more than 2050 minutes for each season (with a 82 games regular season, thats around 25 minutes per game. Players with less than that will be hard to be MVP, and will distort the analysis).
  -Deducted features with too much NaN
  
2. Merge both tables together and calculate PPG,APG,3PG,RPG,FTPG,TOPG,MVP
  -create MVP feature (MVP=1 if VoteShare is bigger than the required VoteRate as well as MVPrate)
  
3. Split the data and Standadized the Features
  -Train data: 1980-1981~2015-2016 season
  -Test data: 2016-2017 season
  
4. Choosing Features
  -plot the numbers of features-accuracy graph and then we can choose the number of features we want to use and then use the "Sequential feature selection algorithms" to find out the features really matters under different methods.
  ![alt text](https://github.com/yipanglin/PHBS_TQFML/raw/master/Project/Cor.png)
  ![alt text](https://github.com/yipanglin/PHBS_TQFML/raw/master/Project/Feature%20Importance.png)
  ![alt text](https://github.com/yipanglin/PHBS_TQFML/raw/master/Project/DecisionTree.png)
  ![alt text](https://github.com/yipanglin/PHBS_TQFML/raw/master/Project/Random%20Forest.png)
  ![alt text](https://github.com/yipanglin/PHBS_TQFML/raw/master/Project/LinearSVC.png)
  ![alt text](https://github.com/yipanglin/PHBS_TQFML/raw/master/Project/SMOTE.png)
  ![alt text](https://github.com/yipanglin/PHBS_TQFML/raw/master/Project/Bagging.png)
  
5. Applying every method to predict MVP candidate in 2016 season, and we can also change the MVPrate to inflence the prediction outcome of MVP I want.



## Problem & Solutions
1. Class Imbalance leads to Accuracy Paradox: It is the case where your accuracy measures tell the story that you have excellent accuracy (such as 90%), but the accuracy is only reflecting the underlying class distribution. In this project, the outcome of nnot being MVP is much much more common than being the MVP, so our models is accurate if it just tells everyone they are not going to be MVP
==> Trying to increase the MVP class or reduce the non-MVP class and choose the model we use.

2. There are a lot of players who have been classified as MVP.
==> Increase the MVPrate.

## Outcome

### MVPrate=0.1(VoteShare>0.1)(True:Russell Westbrook,Kawhi Leonard,LeBron James,James Harden)

-DecisionTree(4/8)
LeBron James, Russell Westbrook, Jimmy Butler, Damian Lillard, Kawhi Leonard, James Harden, Kevin Durant, Giannis Antetokounmpo

-RandomForest(4/7)
LeBron James, Giannis Antetokounmpo, Anthony Davis, Russell Westbrook, Kawhi Leonard, James Harden, DeMarcus Cousins

-LinearSVC(3/4)
LeBron James, Kevin Durant, Russell Westbrook, James Harden

-SMOTE(3/4)
LeBron James, Kevin Durant, Russell Westbrook, James Harden

-Bagging method(4/8)
LeBron James, Russell Westbrook, Anthony Davis, Karl-Anthony Towns, Kawhi Leonard, James Harden, Kevin Durant, Giannis Antetokounmpo

### MVPrate=0.2(VoteShare>0.2)(True:Kawhi Leonard, Russell Westbrook)
-DecisionTree(2/7)
LeBron James, Kawhi Leonard, Kevin Durant, James Harden, Damian Lillard, Jimmy Butler, Russell Westbrook

-RandomForest(2/7)
LeBron James, Russell Westbrook, Jimmy Butler, Kawhi Leonard, James Harden, Kevin Durant, Giannis Antetokounmpo

-LinearSVC(0/1)
James Harden

-SMOTE(0/0)
NaN

-Bagging method(2/5)
LeBron James, Anthony Davis, Kevin Durant, Russell Westbrook, Kawhi Leonard

### MVPrate=0.3(VoteShare>0.3)(True:Kawhi Leonard, Russell Westbrook)

-DecisionTree(2/6)
Kevin Durant, DeMar DeRozan, Stephen Curry, Russell Westbrook, Kawhi Leonard, James Harden
Training accuracy: 0.970442061208475
Test accuracy: 0.9615384615384616

-RandomForest(2/6)
LeBron James, Kevin Durant, Giannis Antetokounmpo, Russell Westbrook, Kawhi Leonard, James Harden
Training accuracy: 0.970442061208475
Test accuracy: 0.9615384615384616

-LinearSVC(1/4)
LeBron James, Kevin Durant, Russell Westbrook, James Harden
Training accuracy: 0.7962333246141774
Test accuracy: 0.9326923076923077

-SMOTE(0/0)
NaN
Training accuracy: 0.7923097044206121
Test accuracy: 0.9326923076923077

-Bagging method(1/3)
LeBron James, Russell Westbrook, James Harden
Training accuracy: 0.970442061208475
Test accuracy: 0.9615384615384616

### MVPrate=0.4(VoteShare>0.4)(True:Russell Westbrook)

-DecisionTree(0/2)
LeBron James, Kawhi Leonard
Training accuracy: 0.9761967041590374
Test accuracy: 0.9711538461538461

-RandomForest(0/0)
NaN
Training accuracy: 0.9761967041590374
Test accuracy: 0.9711538461538461

-LinearSVC(0/3)
LeBron James, Kevin Durant, James Harden
Training accuracy: 0.7588281454355218
Test accuracy: 0.9326923076923077

-SMOTE(0/1)
James Harden
Training accuracy: 0.7590897201150929
Test accuracy: 0.9326923076923077

-Bagging method(0/1)
LeBron James
Training accuracy: 0.9761967041590374
Test accuracy: 0.9711538461538461

I will choose randomforest as my model tp predict MVP in the future.