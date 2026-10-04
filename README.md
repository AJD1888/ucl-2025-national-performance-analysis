# UEFA Champions League Performance Analysis 


## Project Overview

From the 2024/25 season onwards, the format of the group stage of the champions league changed. It moved from 32 teams split into 8 groups of 4, to 36 teams all competing in one league. This increases the number of matches that teams in the competition play. 
Traditionally, the clubs from the top european nations have dominated in this competition, with the last 10 winners being from 4 or the current top 5 european ranked nations based on coefficient (France, Spain, England, Germany). 

This project will investigate wheather the top-ranked UEFA nations, based on coefficient are producing players who peform well at the elite Champions League level, with the aim to conclude if teams from thse nations that perform well in the competition are organically breeding talent or simply hand-picking the best that other nations across the world have to offer. 

## Exploratory Data Analysis

The project uses data from kaggle, linked at the bottom of the document, which contains player data from the first 4 matchdays of the champions legaue "league phase" from the 2024/25 season. The data is split into 10 csv files. These are as follows:

- teams_data.csv : contains all 36 registered teams
- players_data.csv : contains all players registered to play for their respective team in the competition, as well as their nationality and field position. 
- attacking_data.csv : contains attacking related stats for each player 
- defending_data.csv : contains defending relating stats for each player 
- attempts_data.csv : contains all stats relating to attempts on goal for each player 
- disciplinary_data.csv : contains all stats relating to discipline for each player 
- distribution_data.csv : contains all statistics relating to passing for each player 
- goalkeeping_data.csv : contains all goalkeeping related stats for each goalkeeper
- goals_data.csv : contains all stats relating to goals scored for each player
- key_stats_data.csv : cotains distance covered, top speed, minutes played and appearance for each player

To start, all CSV files were read into dataframes using the read_csv() function. After getting a sense for each of the dataframes, any columns that would be not required for our analysis were removed. For example, any cloumns containing images (e.g. team logos and player images) were removed and in the player column we removed weight, height and specific position columns as these contained many NaN values and would not be used in this project. In the case of specific positions, we have another column field_position with four values (goalkeeper, defender, midfielder, forward) which contains all the inforamtion we need when looking to perform analysis on areas of the park that countries specialise in. Any remaing missing data could be filled with the value '0'. While this is normally risky, in our specific case any stats that players don't have a value for (e.g. number of attenpts on goal for a goalkeeper) are all the equivalent of having the value '0' there anyway. 


## Statistical Analysis 

Firstly, some basic statistics relating to volume were looked at. From the data provided, we initially looked at the players with the top 10 goals and assists as well as the combined G/A of players grouped by nationality. While this is insgightful data into how certain individuals performed at the level and what nationalities have the most goal contributions, looking at soley volume provides a bias to larger nations and players that are playing in the best leagues with the best squads. To mitigate this, we want to normalise the data to certain key statistics per 90 minutes or look at certain stats as a percentage (e.g. conversion rate), as this will give a fair representation of how efficient players performed in the competition. In addition to this, any play data we are analysing must only included players that have played at least 180 minutes of football (equivalent to 2 games) to help remove any outliers. This is becacuse for example, if a player had come on for 5 minutes and scored 1 goal and that was the only game they played, they would have 18.0 goals per 90, which wouldn't be fair when comparing them to other players who have played more minutes. The data per 90 for analysis was broken down into specific metrics for each area of the field: 

- Goalkeepers : clean sheets per 90
- Defenders : tackles won (%), ball recoveries per 90
- Midfilders : assists per 90, goals per 90, pass completion rate (%) 
- Forwards : conversion rate (%), goals per 90, assists per 90

Note that these statistics can overlap in some positions. For example, a defender could be in the top 10 assists per 90. 

## Conclusions 

From the visualisation provided, we can see we have some considerations to look at in our analysis. More players from countries outside the top five ranked countries on coefficient played more matches and minutes in the Uefa Champions League. However, this is why the analysis is position specific and only looks at the top 10 players in each of the metrics mentioned, to give a better sense of where the highest peforming players come from. Here were some key findings: 

- Attacking Efficiency : Of the top ten players with the highest goals/90 , eight of them came from a country ranked outwith the top 5 national associations. This was the same ratio for assists/90.
- Goalkeeping reliability : Of the top ten goalkeepers with the highest clean sheets/90, six of them came from outside a top five national association.
- Defensive solidity : Of the top ten players with the highest tackles won (%), the split by top five national associations and other countries was 50/50. 

Core Analytical Takeways: 

1. Volume vs Efficiency: 
While players from the top five national associations provided high total volume (in our case combined G/A) due to club depth and quality of squad, normalising statistics to per-90 rates reveals that elite efficiency is heavily decentralised across global nations. 
2. Best Leagues doesen't mean best players come from that nation
Top quality individual output in the Champions League is not exclusive to traditional powerhouse nations. Players from "other" nations (who potentially play in these leagues) match or exceed players from the top five uefa nations based on coefficient, particularly in the attacking areas of the pitch. 

## Project Limitations 

Several limitations should be considered when interpreting the results: 

- Limited sampe size : The dataset used only covers the first 4 matchdays of the 2024/25 season, representing a relatively small sample size of matches and total minutes played. A fairer representation would have been the 8 matches from the league phase of the competition or including later knockout rounds.
- Early Season Variance : Metrics calculated are suspect to short-term variance, player form spikes and disparities in fixture difficulty.
- Contextual Variables excluded : Per-90 efficiency metrics do not account for external tactical variables such as team playing style, domestic league fatigue, or individual role responsibilites within specific tactical plans. 

## Dataset 
https://www.kaggle.com/datasets/pabloramoswilkins/ucl-2025-players-data


