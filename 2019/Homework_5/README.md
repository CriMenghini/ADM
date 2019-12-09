# Homework 5 - Explore California and Nevada with graphs

![Alt Text](https://1igc0ojossa412h1e3ek8d1w-wpengine.netdna-ssl.com/wp-content/uploads/2018/03/9780921338390.jpg)

In this homework, you will build a system that provides users with information about roads in California and Nevada. Specifically, the implementation of the system consists of two parts. 

* __Backend:__ where you need to develop efficient algorithms that define the *functionalities of the system*
* __Frontend:__ where you provide *visualization for queries entered by the user*

__IMPORTANT:__ In order to deal with graphs you can freely use libraries such as `networkx`, but when you are writing algorithms they have to be implemented by yourself.


## 1. Data collection

The first step, as always, is to download the data you will be working on. You can download the data to build the system [here](http://users.diag.uniroma1.it/challenge9/download.shtml). Download the files for the dataset named **CAL**.
  
  In particular, you will get the following three files containing the below-mentioned information:
  * __Distance graph__ - file containing physical distances between each pair of nodes. Each line follows this structure: *(Id_Node1, Id_Node2, d(Id_Node1,Id_Node2))*, where __d(x,y)__ is the physical distance between x and y.
  * __Travel time graph__ - file containing time distances between each pair of nodes. Each line follows this structure: *(Node1, Node2, t(Id_Node1, Id_Node2))*, where __t(x,y)__ is the time distance between x and y.
  * __Node information file__  - file containing node coordinates. Each line follows this structure: *(Id_Node, Latitude, Longitude)*


## 2. Implementation of the backend

The goal of this part is the implementation of a unique system that has four different functionalities. The program takes in input always a number _i_ in [1,4]: given the input, the program has to run Functionality _i_,  applied to the graph you create from the downloaded data. 

 ### <i> Functionality 1 - Find the Neighbours! </i>

 It takes in input:
 - a node _v_
 - One of the following distances function: **t(x,y)**, **d(x,y)** or **network distance** (i.e. consider all edges to have weight equal to 1).
 - a distance threshold _d_
    
Implement an algorithm (using proper data structures) that returns the set of nodes at distance <= _d_ from _v_, corresponding to _v_’s neighborhood.



 ### <i> Functionality 2 - Find the smartest Network! </i>

 It takes in input:
 
 - a set of nodes _v = {v\_1, ..., v\_n}_
 - One of the following distances function: **t(x,y)**, **d(x,y)** or **network distance** (i.e. consider all edges to have weight equal to 1).

Implement an algorithm that returns the set of roads (edges) that enable the user to visit all the places. We want this set to be the ones whose sum of distances is minimum.

As a dummy example, a set of input could be {Colosseo, Piazza Venezia, Piazza del Popolo} and therefore the associated set of streets will be {Via dei Fori Imperiali, Via del Corso}.


 ### <i> Functionality 3  - Shortest Ordered Route </i>
 
  It takes in input:
 
 - a node _H_
 - A sequence of nodes _p = [p\_1, ..., p\_n]_
 - One of the following distances function: **t(x,y)**, **d(x,y)** or **network distance** (i.e. consider all edges to have weight equal to 1).

Implement an algorithm that returns the shortest __walk__ that goes from _H_ to _p\_n_, and that visits **in order** the nodes in _p_.

Consider that:
- The algorithm needs to handle the case that the graph is not connected, thus not all the nodes in _p_ are reachable from H. In such scenario, it is enough to let the program give in output the string "Not possible".
- Since we are dealing with walks, you can pass more than once on the same node _p\_i_, but you have to preserve order. E.g.: if you pass through _p\_2_ and you are going to _p\_3_, you can pass through _p\_10_, but once you will be in _p\_9_, you will have to go back to _p\_10_ as well.


 ### <i> Functionality 4 - Shortest Route </i>
   
   It takes in input:
 
 - a node _H_
 - A set of nodes _p = {p\_1, ..., p\_n}_
 - One of the following distances function: **t(x,y)**, **d(x,y)** or **network distance** (i.e. consider all edges to have weight equal to 1).

Implement an algorithm that returns the shortest __walk__ that goes from _H_ to _p\_n_, and that visits the nodes in _p_.

Consider that:
- The algorithm needs to handle the case that the graph is not connected, thus not all the nodes in _p_ are reachable from H. In such scenario, it is enough to let the program give in output the string "Not possible".
- Since we are dealing with walks, you can pass more than once on the same node _p\_i_.
- Since the problem’s complexity is high, consider to provide just an approximation/heuristic solution for the problem. 




## 3. Implementation of the frontend

In this section, you build the visualizations for users’ queries results. 

 ### <i> Visualization 1 - Visualize the Neighbours!</i>
 
Once the user runs Functionality 1, we want the system to show in output a complete map that contains: the input node, the output nodes and all the streets that connect these points. Choose different colors in order to highlight which is the input node, and which are the output nodes. Furthermore, choose different colors for edges, according to the distance function used. 

 ### <i> Visualization 2  - Visualize the smartest Network! </i>
 
 Once the user runs Functionality 2, we want the system to show in output a complete map that contains: the input nodes and **all** the edges that connect them. Choose different colors in order to highlight which are the output edges. Furthermore, choose different colors for edges, according to the distance function used. 

 ### <i> Visualization 3 - Visualize the Shortest Ordered Route </i>

 Once the user runs Functionality 3, we want the system to show in output the Shortest Ordered Route.

 ### <i> Visualization 4 - Visualize the Shortest Route </i>
 
Once the user runs Functionality 4, we want the system to show in output the Shortest Route.

For each of the visualization, you can add more 'fancy' stuff. Therefore, you can go deeper, adding more features, and making the visualization even more detailed! But, the important thing is that there are **at least the requested features**.

**Good luck!** 

