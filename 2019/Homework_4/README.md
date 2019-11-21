# Homework 4 - Hard coding

**Goal of the homework**: write important algorithms and function from scratch.

## 1. Hashing task!

For this task we're dealing with hashing algorithms. In particular you will implement **hash functions** and a structure called [***Bloom Filter***](https://en.wikipedia.org/wiki/Bloom_filter).

Nowadays there are so many scenarios where we need to search a little amount of data in large pool of data stored somewhere else. As data scientists, we are expected to optimize that search as much as possible.

Let's say you are creating a new email account in Gmail. Google has to check wether the id you are trying to use is not used by any user around the world. Just imagine, there are billions of email ids stored in Gmail already, is it a feasible approach to scan billions of data in thousands of servers for every new email id? Isn’t it a better idea to approximately guess the status of the provided id? 

**Bloom filter** comes into rescue in this sort of scenario. This space-efficient data structure is used to check very rapidly the membership of an item in a big set of items. The price we pay for efficiency is that it is probabilistic in nature meaning that there might be some **False Positive** results. False positive means, it might tell that given texts are already stored even if they actually aren't.

![alt-text](https://upload.wikimedia.org/wikipedia/commons/thumb/a/ac/Bloom_filter.svg/720px-Bloom_filter.svg.png)

### Your task
Download the datasets [here](https://drive.google.com/file/d/1ymID3fk4aIWKMD2GPYlESy2pimcUkomp/view?usp=sharing). You will find a .zip archive with two quite big files:
* `passwords1.txt`
* `passwords2.txt`

Each row of the files corresponds to a string of 20 characters. The first dataset represents your "pool" of passwords and you will have to find how many passwords of the second dataset are already present in the pool. 

1) Implement your own hash functions by scratch, no ready-made hash functions are allowed, you have to code them by hand. Read the class material and search the internet. The hash function will have to convert the string containing the password to a (potentially large) number.

2) Using your hash function, implement a Bloom Filter structure. [This website](https://hackernoon.com/probabilistic-data-structures-bloom-filter-5374112a7832) is a useful reading.

3) Add the passwords of the first dataset to your filter.

4) Check how many passwords of the second dataset are present in the filter you have created.

5) At the end you will have to provide:
	* The number of ***hash functions*** you have used. 
	* The number of passwords that are ***probably duplicates***.
	* The probability of finding a ***false positive***.
	* The ***execution time*** of your Algorithm. ***[note1](#note-1)***
	
6) [**Bonus**] Can you provide the exact number of ***false positives*** you have found?


#### Note 1

The execution time has to be computed from the beginning to the end of your algorithm. Time starts when you add the first password of the first dataset to the filter, and time stops after checking if the last password of the second dataset is in the filter. Here's an example:

```python

import time

def BloomFilter(passwords1, passwords2):
    start = time.time()
    ...
    
    # add all passwords1 to the filter
    # check all passwords2 presence in the filter
    
    ...
    end = time.time()
    
    print('Number of hash function used: ', k)
    print('Number of duplicates detected: ', n)
    print('Probability of false positives: ', p)
    print('Execution time: ', end-start)
    
BloomFilter(passwords1, passwords2)

```
	
## 2. Alphabetical Sort

Given a set of words, a common natural task is the one of sorting them in alphabetical order. It is something that you have for sure already done once in your life, using your own algorithm without maybe knowing it.

In order to be everyone on the same page, we will refer to the rules defined [here](https://en.wikipedia.org/wiki/Alphabetical_order#Ordering_in_the_Latin_script), subsection "Basic Order and Example". As for multi-word string, let stick with the first policy proposed in subsection "Treatment of multiword strings". Finally, we will use as alphabet the [ISO basic Latin alphabet](https://en.wikipedia.org/wiki/ISO_basic_Latin_alphabet).

What you might know is that we can relate this task to a simple algorithm that runs in linear time: [Counting Sort](https://www.hackerearth.com/practice/algorithms/sorting/counting-sort/tutorial/). Counting Sort is based on a simple assumption: you know the range of the possible values of the instances you have to sort. In this exercise you are asked to perform Alphabetical Sort exploiting the algorithm of Counting Sort.

Therefore:

1) Build your own implementation of Counting Sort. If it's **based** (based, not copied!) on some reference on Internet, please cite it.

2) Build an algorithm, based on your implementation of Counting Sort, that receives in input a list with all the letters of the alphabet (not in alphabetical order), and returns the list ordered according to alphabetical order. Discuss time complexity (theoretically and empirically).

3) Build an algorithm, based on your implementation of Counting Sort, that receives in input a list of length *m*, that contains words with maximum length equal to *n*, and returns the list ordered according to alphabetical order. Discuss time complexity (theoretically and empirically).

## 3. Find similar wines!

In this assignment, the goal is to find set of similar wines according to some characteristics. To perform the task, download this [dataset](http://archive.ics.uci.edu/ml/datasets/Wine) and run a clustering analysis. Clustering can be considered the most important *unsupervised learning problem*; so, as every other problem of this kind, it deals with finding a structure in a collection of unlabeled data.

 **You must implement the k-means (not ++: random initialization) clustering algorithm by yourself from scratch** (**not** with libraries) as explained in the class. Afterward, perform the clustering analysis by using your implementations on the provided dataset. Are the clusters that you get similar?
 
* Plot the distribution of the different features and try to understand the main characteristics of the obtained clusters.
 
**IMPORTANT**: In addition, even though we know you may consult the internet for information about how you could implement an algorithm, the final code must be yours. *Since the task is to design and implement an algorithm for a clustering problem, it is fine and you may use the internet for information about the steps of the algorithm execution and the theory to understand the concept better, as long as you are not searching or copying the code.*
 

### Bonus Clustering
* Implement K-means in Map Reduce!


## 4. K-means can go wrong!

You might know that k-means performances are significantly conditioned by its initialization. Provide an example that shows that with wrong initialization, the cost of the solution produced by the k-means algorithm can be arbitrarily larger from the cost of the optimal solution. You can either code it, or explain it in a **clear** text file.
