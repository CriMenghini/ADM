# Homework 2 - Soccer analytics

Soccer analytics is attracting an increasing interest of academia and industry, thanks to the availability of sensing technologies that provide high-fidelity data streams extracted from every match. 

The __goal__ of this assignment is to perform an analysis on the largest open collection of soccer-logs ever released, collected by [Wyscout] (https://wyscout.com/) containing all the spatio-temporal events (passes, shots, fouls, etc.) that occur during all matches of the entire season 2017-2018 of seven competitions (La Liga, Serie A, Bundesliga, Premier League, Ligue 1, FIFA World Cup 2018, UEFA Euro Cup 2016). A match event contains information about its position, time, outcome, player and characteristics. 

In particular, we are curious to answer to some specific *research questions* (__RQs__) that may help us discover and interpret  meaningful patterns in data.

![alt text](https://www.cumberlandymca.org/uploads/5/2/2/3/52235279/soccer-football-sunset-1-1024x553_orig.jpg "Logo Title Text 1")

____

## Before starting
Among all numerous things and good practises a data scientist needs to do before running any analysis, there is one the is of uttermost importance: __get data and understand it__! 


Here you find the list of tasks you need to perform before digging into the rich world of soccer.

* __Get your data!__ Go to [this website](https://figshare.com/collections/Soccer_match_event_dataset/4415000) and download the files related to **Coaches**, **Players**, **Events**, **Teams** and **Matches**.
	- Throughout the analysis we focus only in **club teams** information. So, there is __no need__ to download/use the files relative to the European Cup and the World Cup.
* __Understand your data.__ Read the legend of each column to understand what it refers to. Additional information about the labels can be found here: [Coaches](https://apidocs.wyscout.com/coaches-wyid), [Players](https://apidocs.wyscout.com/players-wyid), [Events](https://apidocs.wyscout.com/matches-wyid-events), [Teams](https://apidocs.wyscout.com/teams-wyid), [Matches](https://apidocs.wyscout.com/matches-wyid). Please, be sure that you've understood the data before start coding.
* __Handling data.__ The data are provided in multiple `.json` files, with some of the columns present in more than one file. For this reason, in order to answer the RQs, we kindly suggest you to import the `.json` files as `pandas DataFrame` object and then, based on what you want to analyze, perform joins among the DataFrames. Here you can find a quick useful [guide](https://www.datacamp.com/community/tutorials/joining-dataframes-pandas). Remember, Google is your best friend!

____


# VERY VERY IMPORTANT
1. __!!! Read the entire homework before coding anything!!!__
2. _My solution it's not better than yours and yours is not better than mine_. In any data analysis task, there __is not__ a unique way to answer to RQs. For this reason it is crucial (__necessary and mandatory__) that you describe any single decision you take and all the steps you do.
3. Once performed any exercise, comments about the obtained results are **mandatory**. We are not always explicit where to focus your comments, but we will always want some brief sentences about your discoveries.

____

    
    
# Research questions

### Exploratory Data Analysis   

__General Setup__: *All the analysis requested from RQ1 to RQ5, must be performed __only__ over the Premier League dataset.* 

1. [__RQ1__] *Who wants to be a Champion?* During a season could happen that a team has bad periods. For example, more than three consecutive games lost, or it could have a positive trend where it seems to be unbeatable. Let's visualize this trends!

    Create a plot where each point _(x,y)_ represents the number of points obtained by team _x_ at game week _y_. In order to show the trends, points related to the same team must be connected to each other. Remind: in soccer each team gets 3 points for a win, 1 point for a tied game, and 0 for a loss. Highlight the two teams that got the longest winning streak (# of consecutive wins), and the two teams that got the longest losing streak (# of consecutive losses).

    Below you can see a similar example of what we would like you to show us. Keep in mind that you must create this plot for all the entire season (38 game weeks).
 
    <p><img src="http://i.imgur.com/QjvLsKe.png" height="250" align="middle"></p>
   


2. [__RQ2__]  *Is there a home-field advantage?* It is generally believed that there is an underlying home field advantage in sport, i.e. an highest probability of winning of the home team. Let's check for this, and see whether the outcome of the game (win, draw, lose) is correlated to the playing side (home or away). For 5 different teams of Premier League, show the contingency table (_outcome_ x _side_). Therefore, perform an "overall" [*Chi-squared test*](http://learntech.uwe.ac.uk/da/Default.aspx?pageid=1440) in the following way: build a unique contingency table, that contains all the matches in which **only one** of the 5 teams previously selected is involved, to see whether there is home field advantage. State clearly the tested hypothesis and whether it is accepted or rejected. 
 
3. [__RQ3__] *Which teams have the youngest coaches?*  Rank all the teams by the age of their coach and show the 10 teams with the youngest coaches. Remember that during a season a team could have more coaches, in that case pick the younger of them. Additionally, show the distirbutions of the ages of all coaches in Premier League, using a boxplot. (Hint: There's an attribute *birthDate*).

4. [__RQ4__] Find the top 10 players with the highest ratio between completed passes and attempted passes. For this task, consider __all__ the different types of passes, and as specified in the [website](https://apidocs.wyscout.com/matches-wyid-events), a completed pass has tag 1801 (**accurate event**).

    In order to avoid meaningless results (e.g. players who played few minutes, and completed 2 passes over 2, achieving 100% ratio), select an arbitrary threshold of minimum attempted passes, in order to consider only the subset of players that played enough. Justify the choices you make.


5. [__RQ5__] *Does being a tall player mean winning more air duels?* Soccer is a physical game, and it happens often in a match that players are involved in air duels (i.e. when two players are contending for the ball while it is not on the ground). Make a plot that shows the dependency between height of the player and the ratio of air duels won with air duels attempted. The visualization should be a scatterplot, where each point _(x,y)_ represent a player whose height is equal to _x_, and that has a ratio of winning air duels equal to _y_. Furthermore, color any point according an arbitrary selection of categories of height (e.g. yellow: 160-165cm, orange: 165-170cm, etc.)

    Remember that the **"Air Duel"** is a subevent of the event **"Duel"** and that an air duel is said to be won if it has the tag **"1801"**. Same as in RQ4, choose a threshold of minimum air duels attempted, in order filter your data, get reliable results, and justify your choice. 
   

6. [__RQ6__]  *Free your mind!* Go further with the EDA (*Exploratory Data Analysis*) showing a new interesting result about the dataset that you found.
 
### Core Research Questions

- [**CRQ1**] *What are the time slots of the match with more goals?* Let's analyse and visualise the goals distribution into 9-minutes sets for all the matches. I.e., let's transform the minute of a goal from a continuous variable in a discrete variable (e.g. A goal scored in 5th minute, will end up in the interval _\[0-9)_). Remind that every match goes usually from minute 0, to minute 90, but in football it is always added an arbitary amount of extra-time to every half of the match, thus consider also the intervals "45+" and "90+".

	1. Make a barplot with the absolute frequency of goals in all the time slots.
	2. Find the top 10 teams that score the most in the interval "81-90".
	3. Show if there are players that were able to score at least one goal in 8 different intervals.


- [**CRQ2**] *Visualize movements and passes on the pitch!* Here we try to focus our attention on the zones that a player covers during a match. For each event, we have a pair of coordinates, that are respectively the starting and ending point of that event. 
It can be helpful to follow this [link](https://www.towardsdatascience.com/advanced-sports-visualization-with-pandas-matplotlib-and-seaborn-9c16df80a81b/).

Knowing all the different positions where events happen, let us be able to create different types of visualizations:

1. Considering only the match [**Barcelona - Real Madrid** played on the 6 May 2018](https://www.google.com/search?q=barcellona+real+17+18&oq=barcellona+real+17+18&aqs=chrome.0.69i59j0l3.1521j0j7&sourceid=chrome&ie=UTF-8#sie=m;/g/11f53t4vs8;2;/m/09gqx;dt;fp;1;;):
    * visualize with a heatmap the zones where **Cristiano Ronaldo** was more active. The events to be considered are: passes, shoots, duels, free kicks.
    * compare his map with the one of **Lionel Messi**. Comment the results and point out the main differences (we are not looking for deep and technique analysis, just show us if there are some clear differences between the 2 plots).
        
Here's an example of heatmap where are shown all the starting positions of the goals of Arsenal during the entire season.
    
![alt text](https://github.com/CriMenghini/ADM/blob/master/2019/Homework_2/arsenal_goals.png)

2. Considering only the match [**Juventus - Napoli** played on the 22 April 2018](https://www.google.com/search?safe=active&sxsrf=ACYBGNRXZ3i0a1dbj20pdoInsHEUjeYU4A%3A1570814249512&ei=KbmgXb_eHsaUkgX7vrmICA&q=juventus+napoli+2018&oq=juventus+napoli+2018&gs_l=psy-ab.3..0j0i7i30j0j0i7i30l3j0j0i7i30l2j0.4513.5598..6047...0.5..0.105.770.6j2......0....1..gws-wiz.......0i71j0i20i263j0i13.FoNdEGK6ZpY&ved=0ahUKEwj_luaK25TlAhVGiqQKHXtfDoEQ4dUDCAs&uact=5#sie=m;/g/11hcz2kzzt;2;/m/03zv9;tl;fp;1;;):
    * visualize with arrows the starting point and ending point of each pass done during the match by **Jorginho** and **Miralem Pjanic**. Is there a huge difference between the map with all the passes done and the one with only accurate passes? Comment the results and point out the main differences.
    
Here there's an example of a map with arrows. 

![alt text](https://github.com/CriMenghini/ADM/blob/master/2019/Homework_2/arrows.png)



### Theoretical Question

You are given the recursive function splitSwap, which accepts an array a, an index i, and a length n.

```
function splitSwap(a, l, n):
  if n <= 1:
    return
  splitSwap(a, l, n/2)
  splitSwap(a, l+ n /2, n/2)
  swapList(a, l, n)
```
The subroutine swapList is described here:

```
function swapList(a, l, n):
  for i = 0 to n/2:
    tmp = a[l + i]
    a[l + i] = a[l + n/2 + i]
    a[l + n/2 + i] = tmp
```

1. How much running time does it take to execute splitSwap(a, 0, n)? (We want a Big O analysis.)
2. What does this algorithm do? Is it optimal? Describe the mechanism of the algorithm in details, we do not want to know only its final result.

**HINT:** Consider the scenario where len(a) and n are numbers that are a power of 2.


### Bonus
1. Repeat the entire analysis for other leagues (La Liga, Serie A, Bundesliga and Ligue 1), aggregating the results and highlighting the differences you find among the leagues.
2. Make nice visualization using libraries like [Bokeh](https://bokeh.pydata.org/en/latest/) and [Seaborn](https://seaborn.pydata.org/).

