# Homework 5 - Explore Wikipedia's hyperlinks network

In this assignment we analyze the Wikipedia's articles network by applying graph algorithms.


<div style="text-align:center"><img src ="https://cryptobriefing.com/wp-content/uploads/2018/04/Wikipedia-and-Request-Network-enable-donors-to-donate-in-cryptocurrency.jpg" /></div>


**!!!Read the entire homework before coding anything!!!**

## Data and setting
There are many options to collect and build the Wikipedia's underlying network, we rely on the dataset provided [here](https://snap.stanford.edu/data/wiki-topcats.html). For the purpose of our exploration, we do not consider the entire dataset. Instead, we focus on the articles belonging to a subset of categories. 


1.  Download the reduced version of the graph [Wikicat hyperlink graph](https://drive.google.com/file/d/1QVt0aMOFvLjOEm5eKeCxBQUwIU30_NIh/view?usp=sharing). Every row indicates an edge. In particular, the two elements are the source and the target, respectively.
2.  From [this](https://snap.stanford.edu/data/wiki-topcats.html) page download:
	-  `wiki-topcats-categories.txt.gz`: list of pages per category
	-  `wiki-topcats-page-names.txt.gz`: page names


Note that in the reduced version of the network we removed the categories whose number of articles in less than 5000 and more than 30000.

## General notes

1. You will notice that one article might belong to a single category or multiple ones. In the case of multiple appearance, you break the ties uniformly at random. Please, do it before solving any task in the homework.
2. We assume that all edges in the graphs we will consider have weight equal to 1.
2. __All the algorithms__, unless specified, must be implement from scratch.
3. The algorithms should handle exceptions, e.g. what if there is no path between two nodes?
4. Differently from other homeworks, we will execute your functions.


## RQ1 

Build the graph G=(V, E), where *V* is the set of articles and *E* the hyperlinks among them. Then, provide its basic information:
 
- Is the graph directed?
- How many articles are we considering?
- How many hyperlinks between pages exist?
- Compute the average number of links in an arbitrary page. What is the graph [density](https://en.wikipedia.org/wiki/Dense_graph)? Do you believe that the graph is dense or sparse? Is the graph dense?
- Visualize the nodes' degree distribution

## RQ2

Define a function that takes in input:
- A page _v_
- A number of clicks _d_

and returns the set of all pages that a user can reach within _d_ clicks. 

## RQ3

Define a function that takes in input:

- A category _C_
- A set of pages in _C_, _p = {p<sub>1</sub>, ..., p<sub>n</sub>}_

and returns the minimum number of clicks required to reach all pages in _p_, starting from the page _v_, corresponding to the most central article, according to the _in-degree_ centrality, in _C_.

Consider that:
- The algorithm needs to handle the case that the graph is not connected, thus not all the pages in _p_ are reachable from _v_. In such scenario, it is enough to let the program give in output the string "Not possible".
- Since we are dealing with graph exploration, you can pass more than once on the same page _p<sub>i</sub>_.
- Since the problem’s complexity is high, consider to provide just an approximation/heuristic solution for the problem. 
- You can use whatever metrics of centrality.


## RQ4

Given in input two categories: C<sub>1</sub> and C<sub>2</sub>, we get the subgraph induced by all the articles in the two categories. 

- Let _v_ and _u_ two arbitrary pages in the subgraph. What is the minimum set of hyperlinks one can remove to disconnect _u_ and _v_?


## RQ5

Write a function that, given an arbitrary category C<sub>0</sub> as input, returns the list of remaning categories sorted by their distance from C<sub>0</sub>. In particular, the distance between two categories is defined as 

distance(C<sub>0</sub>, C<sub>i</sub>) = median(ShortestPath(C<sub>0</sub>, C<sub>i</sub>))

where ShortestPath(C<sub>0</sub>, C<sub>i</sub>) is the set of shortest paths from each pair of nodes in the two categories.


## RQ6

Write a function that sorts the categories in the graph according to their PageRank (PR). For this task you need to model the network of categories such that you can apply the PR algorithm.


