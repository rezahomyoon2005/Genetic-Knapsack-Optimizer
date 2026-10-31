Genetic Knapsack Optimizer
A Python implementation of a genetic algorithm for the 0/1 Knapsack Problem, with experiments using three crossover strategies: single-point, two-point, and uniform crossover.

The project explores how different crossover methods affect the quality of solutions found by an evolutionary search algorithm. The implementation and experiments are organized in the Jupyter notebook [`genetic.ipynb`](genetic.ipynb).
Problem Overview
Given a set of items, each with a value and a weight, the goal is to choose a subset with the highest total value without exceeding the knapsack's capacity. Each item can be selected at most once.

We represent a candidate solution as a binary chromosome:
- 1 means the item is selected.
- 0 means the item is not selected.
The optimization problem is:
\[
\max \sum_{i=1}^{n} v_i x_i
\]
subject to
\[
\sum_{i=1}^{n} w_i x_i \le C, \qquad x_i \in \{0,1\}
\]
where v_i is an item's value, w_i is its weight, and C is the capacity. With n items, there are 2^n possible binary solutions, so exhaustive search quickly becomes expensive as the problem grows.
How the Algorithm Works
The notebook implements a genetic algorithm with these steps:
1. Population initialization: Create random binary chromosomes and repair any that exceed the weight limit.
2. Fitness evaluation: Calculate each chromosome's total selected value using a dot product.
3. Parent selection: Use tournament selection (k = 5) to choose parents.
4. Crossover: Generate new chromosomes using one of the three crossover strategies.
5. Mutation: Flip individual bits with a configurable mutation rate.
6. Repair: If a chromosome exceeds the capacity, remove selected items with the lowest value-to-weight ratios until it becomes feasible.
7. Elitism: Carry the top three chromosomes into the next generation.
8. Repeat: Continue for the chosen number of generations, tracking the best fitness found.
Crossover Strategies
Method	Description
Single-point	Split two parents at one randomly chosen point and swap the remaining segments.
Two-point	Swap the segment between two randomly chosen crossover points.
Uniform	Use a random mask to choose each gene from one parent or the other.


Each experiment uses the same overall genetic algorithm structure, with the crossover operation changed between sections of the notebook.
Experimental Setup
The test runner in the notebook uses the following values:
Parameter	Value
Population size	60
Generations	100
Mutation rate	0.03
Tournament size	5
Elite chromosomes	3


These values describe the calls made by run_all_tests; the genetic_algorithm functions also define their own default arguments.

The notebook tests the methods on multiple knapsack instances, prints the best fitness and selected item indices for each instance, and plots Best Fitness per Test Case.

In the notebook's written discussion, the two-point crossover method appeared to perform better on the tested cases. This is an observation from those experiments, not a general guarantee that it will always outperform the other methods.
Getting Started
Requirements
- Python 3
- Jupyter Notebook or JupyterLab
- NumPy
- Matplotlib
Install the required packages:
pip install notebook numpy matplotlib
Run the notebook
1. Clone the repository:
   git clone https://github.com/rezahomyoon2005/Genetic-Knapsack-Optimizer.git
   cd Genetic-Knapsack-Optimizer
2. Make sure the input instances are in a folder called knapsack next to genetic.ipynb. If your data is stored elsewhere, change the argument passed to run_all_tests("knapsack").
3. Start Jupyter:
   jupyter notebook genetic.ipynb
4. Run the notebook cells in order to reproduce the three crossover experiments.
Note: The notebook runs its test cases directly from local .txt files. You need to provide those instances if the knapsack directory is not included in your checkout.
Input File Format
Each test instance is a .txt file with the following structure:
<number_of_items> <capacity>
<value_1> <weight_1>
<value_2> <weight_2>
...
<value_n> <weight_n>
For example:
4 10
10 5
7 3
12 6
5 2
The test runner expects filenames with numeric stems (such as 1.txt and 2.txt) because it sorts them by their filename numbers.
Output
For each input instance, the notebook displays:
- The best fitness value found by the genetic algorithm
- The indices of the selected items (zero-based)
- Progress messages during the generations
It also plots the best fitness values across test cases for each crossover experiment.

Because the algorithm is randomized and the notebook does not set a fixed random seed, results may differ between runs.
Project Structure
Genetic-Knapsack-Optimizer/
├── genetic.ipynb       # Implementation and crossover experiments
├── knapsack/           # Input instances (required for the test runner)
│   ├── 1.txt
│   └── ...
└── README.md
The knapsack/ directory above shows the path expected by the notebook; its presence in the repository depends on which files are committed.
Possible Improvements
- Run each crossover method multiple times with different random seeds and compare averages and variability.
- Plot best fitness over generations, alongside comparisons across test instances.
- Compare the genetic algorithm against an exact solver on small knapsack instances.
- Experiment with different mutation rates, population sizes, and selection strategies.
Technologies
Python · NumPy · Matplotlib · Jupyter Notebook
