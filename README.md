# Sudoku Solver

## Project summary and goals

The main goal of this project is to build an intelligent agent that will solve sudoku by  using two powerful techniques in the field of AI: constraint propagation and search

## Step 1: setting up the board
### Naming Conventions
#### Rows and Columns

Since we're writing an agent to solve the Sudoku puzzle, let's start by labelling rows and columns.

* The rows will be labelled by the letters A, B, C, D, E, F, G, H, I.
* The columns will be labelled by the numbers 1, 2, 3, 4, 5, 6, 7, 8, 9. Here we can see the unsolved and solved puzzles with the labels for the rows and columns.
* The 3x3 squares won't be labelled, but in the diagram, they can be seen with alternating colors of grey and white.

<img src="./images/labels.png?raw=true">

### Boxes, Units and Peers

And let's start naming the important elements created by these rows and columns that are relevant to solving a Sudoku:

* The individual squares at the intersection of rows and columns will be called `boxes`. These boxes will have labels 'A1', 'A2', ..., 'I9'.
* The complete rows, columns, and 3x3 squares, will be called `units`. Thus, each unit is a set of 9 boxes, and there are 27 units in total.
* For a particular box (such as 'A1'), its `peers` will be all other boxes that belong to a common unit (namely, those that belong to the same row, column, or 3x3 square).
Let's see an example. In the grids below, the set of highlighted boxes represent units. Each grid shows a different peer of the box at E3.

<img src="./images/peers.png?raw=true">


## Step 2: Encoding the board

Now, in order to implement an agent, let's start by coding the board in Python. Then, we'll code the necessary functions to solve the Sudoku. We'll record the puzzles in two ways — as a `string` and as a `dictionary`.

The string will consist of a concatenation of all the readings of the digits in the rows, taking the rows from top to bottom. If the puzzle is not solved, we can use a . as a placeholder for an empty box.

For example, the unsolved puzzle at the above left will be written as: 
..3.2.6..9..3.5..1..18.64....81.29..7.......8..67.82....26.95..8..2.3..9..5.1.3..

## Step 3: Strategy 1: Elimination

![alt text](https://github.com/LeoAnnArbor/SudokuSolver/blob/master/images/Elimination.png = 250x250)
![alt text](https://github.com/LeoAnnArbor/SudokuSolver/blob/master/images/Elimination_result.png = 250x250)

## Step 4: Strategy 2: Only Choice


## Step 5: Strategy 3: Naked Twins


# Question 1 (Naked Twins)
Q: How do we use constraint propagation to solve the naked twins problem?  
A: When we have 2 boxes in the same unit that allow the same 2 possibilities, we can conclude that no other boxes in the same unit can have those values. Therefore, the steps are: 

* Examine each unit and check for naked twins(pairs of length 2)
* If present then no other box in the unit can contain the 2 digits in each pair and remove the 2 digits from other unsolved peers in the unit.

Applying this rule reduces other boxes' possibilities and thus narrows down the solution space of the whole puzzle.



# Question 2 (Diagonal Sudoku)
Q: How do we use constraint propagation to solve the diagonal sudoku problem?  
A: Diagonal sudoku can be implemented by addition of two extra diagonal units to account for diagonal constraints. The same code will iterate through all the units, and the constraints would thus propagate. More specifically, all the diagonal entries will have the corresponding diagonal entries as their peers. This will result in not accepting solutions that do not satisfy the diagonal constraint. 


### Code

* `solution.py` - You'll fill this in as part of your solution.
* `solution_test.py` - Do not modify this. You can test your solution by running `python solution_test.py`.
* `PySudoku.py` - Do not modify this. This is code for visualizing your solution.
* `visualize.py` - Do not modify this. This is code for visualizing your solution.

### Visualizing

To visualize your solution, please only assign values to the values_dict using the ```assign_values``` function provided in solution.py

