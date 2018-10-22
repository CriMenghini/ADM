# Submit the homework

In this section you find the instruction to submit your group assignment.

## When?
Homework 2 is due on [28th October 2018](http://aris.me/index.php/data-mining-ds-2018). Any homework submitted after the deadline will be subjected to a penalisation with the following schema:

|   Delay  | Penalisation |
|:--------:|:------------:|
|  1 day |     -0.5     |
| 2 days |      -1      |
| 3 days |      -2      |
| 4 days |      -3      |
| 5 days |      -4      |

If you have particular problems to respect the deadline, please contact Aris directly (putting @Cristina in cc) and explain your situation clearly mention your working group.


The maximum score you can get is 5.

## Where?
1. Each group must create a GitHub repository: follow these [steps](https://github.com/CriMenghini/ADM-HW4/blob/master/README.md) (replace ADM-HW4 with the name you give to the repository).

2. Before the deadline you can push in the repository whatever you want. Any push after the deadline will be taken into account for the penalisation.

__Note__ :
* The state of the repository at deadline time corresponds to your submission.
* __[IMPORTANT]__ be sure to compile this [form](https://goo.gl/forms/yhNYjXiGJAR94mTo2) with your group.

## What?

The content of the repository is up to you. The mandatory files are:
* `README.md`: a Markdown file that explains the content of your repository. This is an [example](https://github.com/CriMenghini/Wikipedia/tree/master/Mention). It is important that for each file/folder you say what it contains.
* `Homework_2.ipynb`: a tidy Notebook where you put the code and the comments of your pipeline. Here an [example](https://github.com/CriMenghini/ADA_Homeworks/blob/master/Homework_2/Hw_2.ipynb) of what it should look like. 
    - In general, for the sake of the tidiness of the Notebook, you are encouraged to save yout functions in external .py files that you [import](https://www.programiz.com/python-programming/modules) in the notebook.
    - Upload on GitHub the notebook with the cells already run
    - It might be possible that you do not see some plots. For this reason, we suggest you to put in the `README.md` a link that you create [here](http://nbviewer.jupyter.org/) just copying and paste the url of your notebook on GitHub.

It __must not__ contain:
* The datasets you used (thus you should clearly state in the readme what dataset you used, if any not in the homework description). That's because git allows you to push only dataset smaller of a max size. [Here](https://medium.com/@haydar_ai/learning-how-to-git-ignoring-files-and-folders-using-gitignore-177556afdbe3) a good Medium's post that tells you how to deal with files/directories you do not want to push on GitHub.


## Evaluation parameters 
The homeworks are evaluated respect to these perspectives:
* [__P1__]: Description of your work
* [__P2__]: Quality in terms of readability and efficiency of code
* [__P3__]: Correctness of the results

Specifically, you will assign a score between 1 and 5 to each of these aspects.

### TAs reviews
The TAs will evaluate all the homeworks.
### Peer evaluation
* For each homework, each student reviews the assignment of 1 group
* Your group will get 3 reviews + 1 (TAs)

The homework you should review will be communicate through Slack. Once you have done with the reviews you will send it through a form where you will be ask to tell us the score of the group for each section and provide explanations about your choices.

Since the way which you do the Peer evaluation will be part of you final exam grade, here some example of good reviews:

__Positive__
> [__P1__]: Comments are really clear and still manage to be short.
> [__P2__]: Code is really well written: coincise and efficient (see the matching names function as an example, really smart and short)
> [__P3__]: Results obtained are clear, well illustrated with very communicative and effective plots.

__Negative__
>[__P1__]:  The textual description for the two first two tasks is minimal, but it describes properly the problem at hand,  for those I would hand in a 4.5,  but there's barely any comments for the third task, there's commented code left in the modules and there's even a TODO that's been left in there.  It is likely one of the member that didn't finish his task properly, but it is he job of the team to at least proofread the final version...
[__P2__]:  For the code quality, utilization of libraries is done throughout and the code is concise in what it does. One annoyance  is the fact that head() or tail() wasn't used and the outputs are often longer than what they could be to show the result format.
[__P3__]:  For the results, first task there's a clear error with the number of new cases in liberia for the last period... passing from ~2 new cases a month to ~2k should raise red flags. At least some explanation of why they kept it, especially in a data wrangling task. In the task two, they didn't re-index, they didn't split the scientific classification string or even clean it, it is clear that they went with the solution with the minimal possible effort. In the third task, it is hard to know exactly what was done ineach cases because of a lack of comments, but the result seem good overall.

Examples of bad reviews:
> Good job
Something is missing

The overall review of the homework should contain 2 positive and 2 negative aspects of the assignment you are evaluating.





