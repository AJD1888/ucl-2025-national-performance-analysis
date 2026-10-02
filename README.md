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


