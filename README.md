# UCD-project-final
Data Analytics project with UCD Professional Academy

Project Abstract

This project covers both team and individual player data for the American National Basketball Association (NBA). The team analysis looks at NBA championship winners and runners-up since 1980. The player data looks at all players drafted into the NBA since 1947.

Introduction

NBA data were chosen for this project as, when researching possible projects on the Kaggle website (www.kaggle.com) and through the wider web, many good data sources were readily available for the sport of basketball.
Importantly, there are also many examples available online of Python users creating insightful reports based on NBA data. In many cases these users also shared their Python code and this proved to be a great source of ideas for this project.
One of the project requirements mandated that data be imported from a file and that data be retrieved using online SQL, APIs or web scraping. The volume of NBA related data available online meant that it was a suitable area to pull my data from to meet the requirements of the project.

Dataset

Web Scrape Dataset
The basketball data website www.basketball-reference.com was used to complete one section Project Milestone 2 (Importing. Retrieve data online using SQL, APIs or web scraping). On this website I scraped data from the list of NBA winners, runners-up, key player awards (www.basketball-reference.com/playoffs) and created a DataFrame from this web scrape. This is a website I look at regularly for basketball information and when I researched online, I found that other Python users had web scraped it in the past. A website I found particularly useful was Michael O’Donnell’s work on www.medium.com 1. This website had clear instruction on how to scrape from a basketball data source and how to create a DataFrame from the scrape.

Flat File Import Dataset
The Kaggle website (www.kaggle.com) contained many detailed NBA related data files that I could have used on the project. The .csv file I pulled from this website2 contains player (Date of Birth, Height, Weight, College, Career Start Year, Career End Year) information from which interesting insights could be drawn. Using player data for the flat file import would also act as a counterpoint to the team-based analysis carried out during the web scrape data analysis exercise.

Implementation Process
1.	Data Collection and Review
Looked at the available fields of data for both the web scrape (team based) and flat file import (player based) DataFrames and reviewed all columns of data. Used like .head(), .info(), isnull().sum() initially to see how big and how clean the data I chose for the project was. These initial, basic Python commands were not included in my final Python notebook.
Web Scrape Dataset
The web scrape DataFrame had less columns and rows than the flat file import. Of particular interest to me on this dataset was looking at NBA championship team winners from 1980 until now. This year (1980) was picked as it was the beginning of the Magic Johnson/Larry Bird era in the NBA with many basketball experts agreeing that this was the year when the NBA started to grow in popularity in the USA and globally. Extracting only the post-1980 data from the web scrape would also demonstrate that I could extract and analyse subset of a larger dataset.
Flat File Import Dataset
The player_data.csv file that I pulled from the Kaggle website contained data on all NBA players from 1947 to 2018. To demonstrate being able to work with a larger dataset I decided to use all this player data to gain some insights.
2.	Data Preparation
Web Scrape Dataset
The web scrape DataFrame did not require a lot of tidying up as all data fields were populated correctly. When the data was scraped from www.basketball-reference.com I could see rows 21 and 41 were blank. To tidy this up and remove these empty rows I used the .pop command. The year of NBA championship victory was not included in the web scrape so a for loop was used to add this year to the DataFrame.
Flat File Import Dataset
There were several blank spaces in the college column of the player_data.csv flat file so it was necessary to replace these blanks with the text “No Uni Info”. For these players it is possible that they went straight to the NBA from high school or else the college (university) they attended had not been recorded.
3.	Basic Calculations
Web Scrape Dataset
The following calculations were added to the Python notebook relating to NBA Championship data post 1980:
•	Number of distinct NBA teams that have won a championship between 1980 and 2022
•	Number of NBA championship victories for each team between 1980 and 2022
Flat File Import Dataset
The following calculations were added to the Python notebook relating to NBA player data from 1947 to 2022:
•	Using the weight (in lbs) and height (in inches) the Body Mass Index (BMI) for each NBA player was calculated where BMI using lbs and inches is defined as:
o	BMI = (weight in lbs x 703) / (height in inches x height in inches)
o	Note that the height for each NBA player in the player_data.csv file was given in the form “6 ft 6 inches”. To convert to a numeric, inches value for each player I created another .csv file. This .csv file (“Height_in_inches.csv”) contained 2 columns of data. One column contained every possible height of an NBA player in the “6 ft 6 inches” format. The second column contained the equivalent height in inches: e.g. “6 ft 6 inches” became 78 inches. This .csv file was merged with the player_data.csv data using a ‘many_to_one’ merge
•	The mean BMI per year of start in the NBA was also calculated and added to the final DataFrame for analysis
4.	Basic Analysis & Conclusions
Web Scrape Dataset
Using .count and .sort_values commands on the web scrape information it was possible to see who the most successful NBA teams of the last 42 years were. Creating a vertical bar chart using the seaborn library also helped to visually check these team rankings.
Flat File Import Dataset
A logical argument to differentiate players 7 foot tall or greater from players under 7 foot, coupled with charts from the seaborn library, the BMI functions I had already created and Python function (.mode, .mean, .unique) enabled me to do some basic player analysis on the player_data.csv file and draw some conclusions from the analysis.

Analaysis & Insights
NBA Champions Insights
NBA_Champions_Since_1980.png
•	The Los Angeles Lakers are the most successful NBA team post 1980 when looking at number of NBA Championship Victories
•	13 different NBA teams have won at least one championship since 1980, output from Python notebook shown below:
 
•	Of the 13 different NBA championship winning teams post 1980, 5 have won only one championship each


Individual Player Data Insights
Weight vs Height.png
•	There looks to be a positive correlation between an NBA player’s weight and a player’s height, i.e., the taller a player is, the heavier they are likely to be
•	Overlaying the BMI information for each player shows that there are no players taller than 7 foot 1 inch (85 inches) with a BMI greater than 30 lbs/inches2
•	Similarly there are no NBA player smaller than 5 foot 10 inches (70 inches) with a BMI greater than 30 lbs/inches2

BMI vs Start Year.png
•	This chart shows some obvious trends for BMI when looking across almost 80 years of player data:
o	BMI remained relatively constant for about 20 years until the late 1960s/early 1970s
o	BMI then started to drop until around 1980
o	From 1980 until around 2000 the BMI started rose from a mean of around 23 lbs/inches2 to 25 lbs/inches2 
o	BMI then remained constant for around 10 years, followed by a spike in 2010
o	BMI has been dropping from 2010 until the end of the dataset in 2018
Note: One limitation on this dataset is that it only considers a player’s weight at the start of their career. If the weight of a player fluctuates during their career, this is not accounted for in the dataset.

Top 10 Colleges.png
•	This chart shows that the University of Kentucky has provided the most players to the NBA since 1947
•	473 colleges have provided players to the NBA since 1947:
•	Of the top 10 colleges to provide players to the NBA, it is interesting to note that University of Notre Dame has yet to have a player 7 foot or taller play in the NBA
•	For the University of Notre Dame player data, it is seen that the #1 mode value for weight of University of Notre Dame players is 185 lbs. This is over 10% lower than the mean weight of all players drafted since 1947 of 209 lbs:
 

Height by Position.png
•	This chart shows that Centres are the tallest players in the NBA. All outliers on the taller side are Centres also
•	This chart shows that Guards are the shortest players in the NBA. All outliers on the shorter height side are Guards

 
References
1.	https://medium.com/analytics-vidhya/intro-to-scraping-basketball-reference-data-8adcaa79664a
2.	https://www.kaggle.com/code/johndkearns/starter-nba-players-stats-since-1950-d424e5b4-0/data?select=player_data.csv


