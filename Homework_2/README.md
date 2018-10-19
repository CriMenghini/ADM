# Homework 2 - How do Taxis move in NYC? 
In this assignment we perform an analysis of Taxis in NYC. In particular, we are curious to answer to some specific *reasearch* questions (__RQs__) that may help Taxi drivers in planning their movements throughout the city and the Taxi's users to have hints about the convenience of enjoying this service.

For this purpose we use the open data of Taxi's trips in NYC. In order to answer to the *RQs* we take into account the data related to Yellow cab for the year 2018.

____

## Before starting
Here you find the list of task you need to perform before running the analysis.

1. Download [Yellow cabs data](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).
2. Due to the size of the file, you will experience that fit all this data in memory is hard. Above all, if you are able to load data in memory, it's gonna be hard to run any analysis. For these reasons, before starting we really encourage you to take a look at the *RQs* and afterwords think of a strategy to deal with data.
* In order to do the analysis by borough you need to combine the *Yellow cabs data* with the dataset you find in `taxi_zone_lookup.csv`.
* Observe the dataset:
    * Read the legend of each columns to understand the data: [link 1](http://www.nyc.gov/html/tlc/downloads/pdf/data_dictionary_trip_records_yellow.pdf)
    * Read something about Yellow Taxis in NYC to make meaningful statements and comments, , [link 2](http://www.nyc.gov/html/tlc/downloads/pdf/taxi_information.pdf).
* Get an [overview](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.describe.html) of the dataset, what are the variable types? May we need to change something?  E.g. some trips register distance 0, does it make sense?
* Check the presence of NaN values and decide how to deal with them (do I esclude the from the analysis?)

____ 

# VERY VERY IMPORTANT
1. __!!!Read the entire homework before coding anything!!!__
2. As any data analysis task, there __is not__ a unique and correct way to answer to our RQs. Since the results you get for each RQ may depend on choices you make during the analysis, it is very important (__necessary__) that you describe any single decision you take and all the steps you do.
____



# General notes:
* At the beginning of your analysis, decide and clearly state what borough you consider for running the analysis: the borough of departure or the arrival one.
* When you are asked to run statistical test, pay attention to the assumptions that must hold to run it. E.g. do the sample distributions have a bell shape (visually is enough)?
* For any  run statistical test you must provide the test hypotesis and clearly say if the null hypothesis is rejected or not.

____

# Research questions

### Exploratory Data Analysis
1. [__RQ1__]  *In what period of the year Taxis are used more?* Create a plot that, for each month, shows the average number of trips recorded each day. Due to the differences among New York zones, we want to visualize the same information for each boroughs. Do you notice any differce among them? Provide comments and plausible explanations about what you observe (*e.i. what is the month with the highest daily average?*). To assess whether the difference of the average daily number of trips among boroughs is [statistically significant](https://en.wikipedia.org/wiki/Statistical_significance), you should run a statistical test (you don't need to perform the test for each possible pair of boroughs, just choose those you are more interested in). Here useful link to get know of a statistical test: [link 1](https://towardsdatascience.com/inferential-statistics-series-t-test-using-numpy-2718f8f9bf2f), [link 2](https://machinelearningmastery.com/parametric-statistical-significance-tests-in-python/).

2. [__RQ2__] *What are the time slots with more passengers?* Set your own time slots and discover which are those when Taxis drive the highest number of passengers overall New York and repeat the analysis for each borough. Provide the results through a visualization and comment them. 

3. [__RQ3__] *Do the all trips last the same?* Let's put our attention on the distribution of trip's duration. Provide a plot for it and comment what you see. Run this analysis for NYC and for each borough (and obviously comment the results!). Eventually, run a statistical test to see if the difference of each borough average respect to the overall one is statistically significant.

4. [__RQ4__] *What is the most common way of payments?* Discover the way payments are executed in each borough and  visualize the number of payments for any possible means. Then run the [*Chi-squared test*](http://learntech.uwe.ac.uk/da/Default.aspx?pageid=1440) to see whether the method of payment is correlated to the borough. Then, comment the results.

5. [__RQ5__] *Does a long distance correlate with the duration of the trip on average?* Make a plot that show the dependence between distance and duration of the trip. Then compute the [Pearson Coefficient](https://en.wikipedia.org/wiki/Pearson_correlation_coefficient), is it significant? Comment the results you obtain.

### Core Research Questions

1. [__CRQ1__]: *Does the fare for kilometer change across NY's borough?* We want to discover whether the expenses of a user that enjoys Taxis in one zone is different from those that uses it in another one. 
    * Considering the fare amount, we want to compute the price per kilometer for each trip ($P'_{km}$):
        - Run the mean and the standard deviation of the variable. Then plot the distribution. What do you see?
        - Run a statistical test that checks if the average price for kilometer in each borough is significally different from the average price in New York
        - Can you say that statistically significant differences, on the averages, hold among zones? In other words, are Taxis trip in some boroughs, on average, more expensive than others? 
    * The price per kilometer might depend on traffic the Taxi finds on its way. So we try to mitigate this effect:
        - Likely, the duration of the trip says something about the city's congestion, especially if combinated with the distances. Thus, it might be a good idea to weight the price for kilometer using the average time needed to travel one kilometer:
        $P''_{km} = \mu *P'_{km}$
        - Run the mean and the standard deviation of the new variable. Then plot the distribution. What do you see?
        - Run a statistical test that checks if the average *weighted* price for kilometer in each borough is significally different from the average price in New York
        - Can you say that statistically significant differences, on the averages, hold among zones? In other words, are Taxis trip in some boroughs, on average, more expensive than others?            
    * Compare the results obtained for the price per kilometer and the weighted price for kilometer. What do you think about that?
    
2. [__CRQ2__]: *Visualize Taxis movements!* NYC is divided in many Taxis zones. For each yellow cab trip we know the zone the Taxi pick up and drop off the users. Let's visualize, on a [chropleth map](https://en.wikipedia.org/wiki/Choropleth_map), the number of trips that starts in each zone. Than, do another map to count the races that end up in the single zone. Comment your discoveries. To perform this task we use the library [`folium`](https://github.com/python-visualization/folium). You find some examples of chorophlet maps [here](https://nbviewer.jupyter.org/github/python-visualization/folium/blob/master/examples/Colormaps.ipynb) and [__here__](https://medium.com/@austinlasseter/using-folium-to-generate-a-simple-map-of-your-pandas-data-87ddc5d55f8d). The `Geojson` we use to trace the zones is `taxi_zones.json` in the Homework's repository.


### Bonus
1. Repeat the entire analysis for other years highlighting the differences you find.
2. Go further with the EDA (*Exploratory Data Analysis*) showing new interesting stuff about the dataset.
3. Make nice visualization using libraries like [Bokeh](https://bokeh.pydata.org/en/latest/) and [Seaborn](https://seaborn.pydata.org/).


