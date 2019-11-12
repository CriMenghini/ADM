# Submit the homework

In this section you find the instruction to submit your group assignment.

## When?
Homework 3 is due on __17th November 2019 - 23:59:59__. Any homework submitted after the deadline will be subjected to a penalisation with the following schema:

|   Delay  | Penalisation |
|:--------:|:------------:|
|  1 day |     -0.5     |
| 2 days |      -1      |
| 3 days |      -2      |
| 4 days |      -3      |
| 5 days |      -4      |




The maximum score you can get is 5.

## Where?
1. Each group must create __only one__ GitHub repository: follow these [steps](https://github.com/CriMenghini/ADM-HW4/blob/master/README.md) (replace ADM-HW4 with the name you give to the repository). Once created the repository, in order to let us know which is your official repository, compile this [form](https://forms.gle/gwr9XGEQsCcApJFEA).

2. Before the deadline you can push in the repository whatever you want. Any push after the deadline will be taken into account for the penalisation.

3. If you have particular problems to respect the deadline, please contact Aris directly (putting @Cristina and @Tommaso in cc) and explain your situation clearly mention your working group. Otherwise, __the state of the repository at deadline time will correspond to your submission__.

## What?

The content of the repository is up to you. The mandatory files are:

* `README.md`: a Markdown file that explains the content of your repository. This is an [example](https://github.com/CriMenghini/Wikipedia/tree/master/Mention). It is important that for each file/folder you say what it contains. [Here](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) a cheatsheet to use Markdown.

* `collector.py`: a python file that contains the line of code needed to collect your data from the `html` page (from which you get the urls) and Wikipedia.
* `collector_utils.py`: a python file that stores the function you used in `collector.py`.
* `parser.py`: a python file that contains the line of code needed to parse the entire collection of `html` pages and save those in `tsv` files.
* `parser_utils.py`: a python file that gathers the function you used in `parser.py`.
* `index.py`: a python file that once executed generate the indexes of the Search engines.
* `index_utils.py`: a python file that contains the functions you used for creating indexes.
* `utils.py`: a python file that gather functions you need in more than one of the previous files like (`collector`, `parser`, etc.)
* `main.py`: a python file that once executed build up the search engine. This file is very important because it is going to be the one you will launch during the exam, ideed you will perform live queries on your search engine. In order to let everything go the best, you have to be sure that the engine will work on pre-computed indeces. Thus, **forget to allow the main file to build the index from scratch**. When the user executes the file it should be able to choose:
	* `search_engine`: a parameter that the user set to choose the search engine to run. According to the request of the homework, you can get 1,2 or 3.
	* Any other parameters you would like.
* `exercise_4.py`: python file that contains the implementation of the algorithm that solves problem 4.

* `main.ipynb`: a Jupyter notebook explaines the strategies you adopted solving the homework and the Bonus point (visualization task). The notebook must be clear, complete and tidy. [Here](https://github.com/dusicastepic/ADMSecondHomework/blob/master/ADM_HW2_Full.ipynb) an example of a nice notebook from last year. **Avoid** pushing on GitHub notebook that contain entire long printed list, otherwise we will not be able to open it.

**[READ IT CAREFULLY]** It __must not__ contain:

* The datasets you used (thus you should clearly state in the readme what dataset you used, if any not in the homework description). That's because git allows you to push only dataset smaller of a max size. [Here](https://medium.com/@haydar_ai/learning-how-to-git-ignoring-files-and-folders-using-gitignore-177556afdbe3) a good Medium's post that tells you how to deal with files/directories you do not want to push on GitHub.

## Post Homework

Each member of the team will need to fill other 2 forms, that will be published after the deadline of the homework:

1. Individual Feedback: a form to express how you worked with your group, and who did what.
2. Peer Review: you will receive an email, containing an homework that you have to review. You will find the guidelines of the review in the form.

You will have __5 days (120 hours)__ to fill the two forms. They are __mandatory__, i.e. we will not grade your homework if you won't fill all the forms.

