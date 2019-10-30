# Homework 3 - What movie to watch tonight?

<p align="left">
<img src="https://d3c1jucybpy4ua.cloudfront.net/data/63462/big_picture/popcorn.jpg?1567006493" height=430 
</p>
 
**Goal of the homework**: *Build a search engine over a list of movies that have a dedicated page on Wikipedia.*


## 1. Data collection

For this homework, there is no provided dataset, but you have to build your own. The data collection task is divided into **three** subtasks.

**IMPORTANT:** since the operation will require some time. Almost hundread students will make lot of request to Wikipedia, we have to absolutely avoid them to block definitely the Sapienza network. Thus, please use download your data from home, if you have issue with WiFi at home text Cristina or Tommaso (@patk, @tommaso).


### 1.1. Get the list of movies

You are given several html pages in the folder `data`. If you open one of them, you should see a list of `urls` of Wikipedia pages, and each one of them refers to a specific movie.

Your first subtask is to **parse** the `html` page and **get** the complete list of `urls`. According to the number of members of your group, you have to parse the first *n* files, where *n* is the number of the members of your group.

### 1.2. Crawl Wikipedia

At this point, you obtained *n* different lists of `urls`. Now we want you to go inside each one of this `url`, and to crawl specific informations from them. 

#### Important
*Due to the large amount of pages you need to download, it is of uttermost importance that you follow few rules we are giving to you. If you do not stick to them, you will not be able to collect efficiently data.*

1. **[Save time downloading files]** You are asked to crawl tons of pages, and this will take a lot of time. To speed up the operation, we suggest you to proceed as follows: each member of the group has to be in charge for only one of the files, such that you are able to work in parallel. The code must be unique, but each one of the members of the group should apply it to its list of urls. **PAY ATTENTION:** Once obtained all the pages, merge your results in a unique dataset. In fact, the search engine must look up for results in the whole set of documents.

2. **[Don't get blocked by Wikipedia]** Wikipedia allows you to crawl their page, but does not allow you to make to many requests in a row. So **first**, wait a random time between 1 and 5 seconds each request (make use of [`time.sleep()`](https://www.journaldev.com/15797/python-time-sleep) Python function). **Second**, the request snippet of code should handle the rise of an exception, that will come up when you will reach the limit of requests of Wikipedia. If the exception happens, you should stop the program for **twenty minutes** (again, with `time.sleep()`) before proceeding with the next slot of requests. The expected run-time for this operation (for each file) is ~**8** hours, and the expected quantity of data is ~**3.5** GB.

3. **[Save your data]** It is not nice to restart a crawling procedure, given its runtime. For this reason, it is extremely important that for every time you crawl a page, you **must** save it with the name `article_i.html`, where `i` corresponds to the number of articles you have already downloaded. In such way, if something goes bad, you can restart your crawling procedure from the *i+1*-th document.
 
### 1.3 Parse downloaded pages

Now that all the movies' Wikipedia pages are stored on your laptop, it is time to parse them and extract the information of interest.

For each Wikipedia Page you should get:

1. Title
2. First two paragraphs of the article. We will refer to them respectively as `intro` and `plot`.
3. The following informations from the **infobox**: film_name, director, producer, writer, starring, music, release date, runtime, country, language, budget.

Those info has to be saved into different `.tsv` files of this structure:

```
title \t intro \t plot \t info_1 \t info_2 \t info_3 \t info_4 ... \t info_n
```

__Example__:
  
```
title \t ... \t  director \t language 
    
harry potter \t ... \t jojo \t english
```

**Be careful** Not all the pages will have the same informations inside the infobox. Wikipedia declares [here](https://en.wikipedia.org/wiki/Template:Infobox_film) all the possible informations you can find there. If you do not find one of the requested informations, just set the value for that observation as `NA`.

## 2. Search Engine

Now, we want to create two different Search Engines that, given as input a query, return the movies that match the query.

As a first common step, you must preprocess the documents by

1. Removing stopwords
2. Removing punctuation
3. Stemming
4. Anything else you think it's needed

For this purpose, you can use the [nltk library](https://www.nltk.org/).

### 2.1. Conjunctive query
At this moment, we narrow our interest on the `intro` and `plot` of each document. It means that the first Search Engine will evaluate queries with respect to the aforementioned information.

#### 2.1.1) Create your index!

Before building the index, be sure you have a file named `vocabulary`, in the format you prefer, that maps each word to an integer (`term_id`).
Then, the first brick of your homework is to create the Inverted Index. It will be a dictionary of this format:

```
{
term_id_1:[document_1, document_2, document_4],
term_id_2:[document_1, document_3, document_5, document_6],
...}
```
where _document\_i_ is the *id* of a document that contains the word.

__Hint:__ Since you do not want to compute the inverted index every time you use the Search Engine, it is worth to think to store it in a separate file and load it in memory when needed.

#### 2.1.2) Execute the query
Given a query, that you let the user enter:

```
disney movies 2019
```

the Search Engine is supposed to return a list of documents.

##### What documents do we want?
Since we are dealing with conjunctive queries (AND), each of the returned documents should contain all the words in the query.
The final output of the query must return, if present, the following information for each of the selected documents:

* Title
* Intro
* Url

__Example Output__:

| Title | Intro | Wikipedia Url |
|:-----------------------------:|:-----:|:-----------------------------------------------------------:|
| Toy Story 4 | ... | https://en.wikipedia.org/wiki/Toy_Story_4 |
| The Lion King | ... | https://en.wikipedia.org/wiki/The_Lion_King_(2019_film) |
| Dumbo | ... | https://en.wikipedia.org/wiki/Dumbo_(2019_film) |

If everything works well in this step, you can go straight to the next point, and make your Search Engine more complex and better in answering queries.


### 2.2) Conjunctive query & Ranking score

In the new Search Engine, given a query, we want to get the *top-k* (the choice of *k* it's up to you!) documents related to the query. In particular:

* Find all the documents that contains all the words in the query.
* Sort them by their similarity with the query
* Return in output *k* documents, or all the documents with non-zero similarity with the query when the results are less than _k_. You __must__ use a heap data structure (you can use Python libraries) for maintaining the *top-k* documents.

To solve this task, you will have to use the *tfIdf* score, and the _Cosine similarity_. Let's see how.


#### 2.2.1) Inverted index
Your second Inverted Index must be of this format:

```
{
term_id_1:[(document1, tfIdf_{term,document1}), (document2, tfIdf_{term,document2}), (document4, tfIdf_{term,document4}), ...],
term_id_2:[(document1, tfIdf_{term,document1}), (document3, tfIdf_{term,document3}), (document5, tfIdf_{term,document5}), (document6, tfIdf_{term,document6}), ...],
...}
```

Practically, for each word you want the list of documents in which it is contained in, and the relative *tfIdf* score.
__Tip__: *tfIdf* values are invariant with respect to the query, for this reason you can precalculate them.

#### 2.2.2) Execute the query

Once you get the right set of documents, we want to know which are the most similar according to the query. For this purpose, as scoring function we will use the Cosine Similarity with respect to the *tfIdf* representations of the documents.

Given a query, that you let the user enter:
```
disney movies 2019
```
the Search Engine is supposed to return a list of documents, __ranked__ by their Cosine Similarity with respect to the query entered in input.

More precisely, the output must contain:
* Title
* Intro
* Url
* The similarity score of the documents with respect to the query


__Example Output__:

| Title | Intro | Wikipedia Url | Similarity |
|:-------------:|:-----:|:-------------------------------------------------------:|------------|
| Toy Story 4 | ... | https://en.wikipedia.org/wiki/Toy_Story_4 | 0.96 |
| The Lion King | ... | https://en.wikipedia.org/wiki/The_Lion_King_(2019_film) | 0.92 |
| Dumbo | ... | https://en.wikipedia.org/wiki/Dumbo_(2019_film) | 0.87 |

## 3. Define a new score!

Now it's your turn. Suppose that some big IT company wants you in their team, but they need the best idea ever on how to rank films based on the queries of their users.

In this scenario, a single user can give in input more information than the single textual query, so you need to take into account all this information, and think a creative and logical way on how to answer at user's requests.

Practically:

1. The user will give you for sure a text query. As a starting point, get the query-related documents by exploiting the search engine of Step 3.1.
2. Once you have the documents, you need to sort them according to your new score. In this step you won't have anymore to take into account just `intro` and `plot` of the documents, you __must__ use the remaining variables in your dataset (or new possible variables that you can create from the existing ones...). You __must__ use a heap data structure (you can use Python libraries) for maintaining the *top-k* documents.

    > __Q:__ How to sort them?
    __A:__ Allow the user to specify more information, that you find in the documents, and define a new metric that ranks the results based on the new request.
   
__N.B.:__ You have to define a __scoring function__, not a filter! 

The output, must contain:

* Title
* Intro
* Url
* The similarity score of the documents according to your score
____


## 4. Algorithmic question
 
You are given a string, *s*. Let's define a subsequence as the subset of characters that respects the order we find them in *s*. For instance, a subsequence of "DATAMINING" is "TMNN". Your goal is to **define and implement** an algorithm that finds the length of the longest possible subsequence that can be read in the same way forward and backwards. For example, given the string "DATAMININGSAPIENZA" the answer should be 7 (d**A**tam**ININ**gsap**I**enz**A**).



**Have fun!**

