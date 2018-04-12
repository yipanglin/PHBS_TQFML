# PHBS_TQFML - Final Project

# Topics
"Who will be the MVP candidates in NBA this season?"

# Reason
1. a big fan of NBA
2. Basketball players across different positions can be measured using the same set of statistics, but like volleyball is very hard.

# What is MVP
The National Basketball Association (NBA) Most Valuable Player Award (MVP) is an annual National Basketball Association (NBA) award given to the best performing player of the regular season.

# How to choose MVP - Voting and voting system
By voting!
Since the 1980–81 season, the award is decided by a panel of sportswriters and broadcasters throughout the United States and Canada.
Each member of the voting panel casts a vote for first to fifth place selections. Each first-place vote is worth 10 points; each second-place vote is worth seven; each third-place vote is worth five, fourth-place is worth three and fifth-place is worth one.

# Voting based on...
Steve Aschburner: "The MVP is the best player on the team with the best record."
Fran Blinebury: "Consistent individual excellence combined with team leadership and more than a few moments of transcendent brilliance."
John Schuhmann: "My vote went to the individual who had the biggest effect on why a good team was good."
Ian Thomsen: "I love this award because it’s all about value: who has done the most for his team?"

We can know that the media vote the MVP based on the contribution of the player to the team, which can be observed from personal statistics and team winning percentage (team standing).

# Project Goal
To predict MVP candidates in 2017-2018 season by training model using classfication from MVP candidates and other players .

# Data
A. What kind of data do I need?
  1. Individual Stats (with Past MVP winners records) (@Seasons_Stats.csv)
  2. Team Stats (@nbastandings.csv)
  3. Voting Stats (@nbavoting.csv)
Data are from basketball-reference.com and Kaggle dataset "NBA Players stats since 1950", with stats for all players since 1950. 

B. Data Choosing
  1. Data from 1980-1981 season to 2016-2017 season, because nowadays voting system was established at 1980-1981 season.
  2. Use the highest five vote-points candidates vs. other players to classify data.
  
# Features:

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

@nbastandings.csv
1. Numbers of winning games (W)
2. Numbers of losing games (L)
==> I will combine them to winning rate.

@nbavoting.csv
1. First-place vote (First) - The numbers of first-place vote.
2. Points won (Pts Won) - The total voting points won by the player.
3. Points max (Pts Max) - The max voting points each player can get at that season.

# Methods
Try KNN/Logistic/SVM/RandomForest/Rogistic method to choose a better model to predict the MVP.