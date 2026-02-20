

---

# 🎒 Knapsack Problem Solver using Genetic Algorithm (GA)

This project explores the application of **Genetic Algorithms** to solve the classical **Knapsack Problem**, an NP-hard combinatorial optimization problem. The goal is to select a subset of items with given weights and values to maximize the total value without exceeding the knapsack's capacity.

## 📝 Project Overview

The implementation focuses on comparing different genetic operators and selection strategies to find the most efficient way to reach the optimal solution.

### Key Components:

* **Fitness Function:** Evaluates the total value of selected items.
* **Repair Mechanism:** A smart repair function that handles capacity violations by removing items with the lowest value-to-weight ratio.
* **Selection Methods:** Includes Tournament Selection and Roulette Wheel Selection.
* **Crossover Strategies:**
* Single-point Crossover
* Multi-point Crossover
* Uniform Crossover


* **Mutation:** Introduces genetic diversity to prevent premature convergence.

## 🛠️ Features

* **Comparative Analysis:** The notebook compares three different crossover methods, concluding that **Multi-point Crossover** generally performs best for this problem.
* **Diversity Management:** Discussion on how mutation rates and selection strategies help escape local optima.
* **Visualization:** Plots showing the convergence of the fitness value over generations.

## 🚀 How to Run

1. Ensure you have Python installed.
2. Install the required libraries:
```bash
pip install numpy matplotlib

```


3. Open `genetic.ipynb` in Jupyter Notebook or VS Code and run the cells.

## 📊 Results Summary

* **Best Performing Method:** Multi-point Crossover.
* **Optimization Goal:** Maximize value while strictly respecting the weight limit (`capacity`).
* **Insight:** The repair function significantly improves the efficiency of the search by keeping the population within the feasible region.

---
