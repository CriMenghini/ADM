# Homework 4

## 1) Does basic house information reflect house's description?

In this assignment we will perform a clustering analysis of house announcements in Rome from Immobiliare.it. Be careful you may notice that the announcement is written in Italian. Don't worry about it, you don't need to understand what's in it.

![alt text](https://directionscu.org/wp-content/uploads/2018/08/cashforhome.png "Logo Title Text 1")

____ 

# VERY VERY IMPORTANT
__!!!Read the entire homework before coding anything!!!__

__We strongly suggest you to run the entire scraping procedure at your place!__
____

### Goal
 You will implement two clustering and compare the results you get. You will need to create two datasets and each of them will be filled by data that you scraped.

### Scraping
This time, you must create your dataset. The website that you will scrape is: [here](https://www.immobiliare.it). In particular, you should retrieve at least 10k announcements starting from this [link](https://www.immobiliare.it/vendita-case/roma/?criterio=rilevanza&pag=1).
The information that you need to extract is explained afterwords. Remember, whenever you have text to work on, do some pre-processing. Use the [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) library to parse the `html`. Make sure to put a [`time.sleep(t)`](https://www.tutorialspoint.com/python/time_sleep.htm), where *t* is the number of seconds, to prevent the website block. It might take a while, be patient.


### Datasets 
#### 1) Information
The first matrix will have this format: <img src="https://latex.codecogs.com/gif.latex?$m_{ij}&space;=&space;value$" title="$m_{ij} = value$" /> where <img src="https://latex.codecogs.com/gif.latex?$i&space;\in&space;\{announcement_1,&space;...,&space;announcement_n\}$" title="$i \in \{announcement_1, ..., announcement_n\}$" /> and <img src="https://latex.codecogs.com/gif.latex?$j&space;\in&space;\{price,&space;locali,&space;superficie,&space;bagni,&space;piano&space;\}$" title="$j \in \{price, locali, superficie, bagni, piano \}$" />. *n* is the number of the announcements. It's possible that not all the announcements will have all the fields mentioned above, if it's the case don't take it into account. 

#### 2) Description
The second matrix will have this format: <img src="https://latex.codecogs.com/gif.latex?$m_{ij}&space;=&space;tfIdf_{ij}$" title="$m_{ij} = tfIdf_{ij}$" /> where <img src="https://latex.codecogs.com/gif.latex?$i&space;\in&space;\{announcement_1,&space;...,&space;announcement_n\}$" title="$i \in \{announcement_1, ..., announcement_n\}$" /> and <img src="https://latex.codecogs.com/gif.latex?$j&space;\in&space;\{word_1,&space;...,word_m\}$" title="$j \in \{word_1, ...,word_m\}$" />. *n* is the number of the announcements and *m* is the cardinality of the vocabulary. This time, you must implement the *Tf-Idf* by yourself (not with libraries). Make sure to use the complete description inside the link of the announcement: [example](https://www.immobiliare.it/69900102-Vendita-Bilocale-viale-Ezra-Pound-Roma.html).

### Clustering
This step consists in clustering the house announcements using K-means++. In order to do that you can use [this](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html) Python library. Choose the optimal number of clusters using the [Elbow-Method](https://en.wikipedia.org/wiki/Elbow_method_(clustering)).

### Comparison among cluster
We expect that both datasets will lead to similar clusters. Is this true?
#### Find similar clusters
To check this, use the Jaccard-Similarity to measure the similarity betweeen the two outputs (information clusters vs description clusters). Return the 3-most similar couples of clusters.
#### Word cloud of house descriptions
With this last output you must create a [wordcloud](https://www.datacamp.com/community/tutorials/wordcloud-python) for each couple of clusters. The words that will be represented are those extracted from the description of the houses that are in the relative couple.

<div style="text-align:center"><img src ="https://d791hlskfkbjh.cloudfront.net/7731287/980x.jpg" /></div>

### Bonus Clustering
* Implement the K-means algorithm (not ++: random initialisation) from scratch (without the library you used before). Are the clusters that you get similar to the ones you previously obtained?
* Implement K-means in Map Reduce!

## 2) Find the duplicates!

You are given [`passwords2.txt`](https://drive.google.com/open?id=1wTmOU-yqk4qdQYg42AquhzgpNGrRA96d) file as input. Each row corresponds to a string of 20 characters. Define a hash function that associates a value to each string. In this case, the goal is to check whether there are some duplicate strings. Our definition of duplicate is that the two strings have the __same characters__, order is not important. Thus, "AABA" = "AAAB".

There are 3 steps that you need to perform:
1. Convert the string containing the password to a (potentially large) number
2. Use a hash function to map the number to a large range. Read the class material and search the internet for this part (but you need to write the code yourself).
3. After having defined the hash function, find if two numbers fall on the same range

* In the file there are 10M duplicates, can you detect them?
* Does it happen that two strings with different characters are hashed to the same value? If yes, could you provide the number of *False Positive*?

Now do the same thing as before, but now the order of the characters must be put into account. Example: "AABA" != "AAAB".
