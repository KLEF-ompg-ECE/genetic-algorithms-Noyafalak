# Assignment 2 — Genetic Algorithm: Knapsack Problem
## Observation Report

**Student Name  :** Noya Falak  
**Student ID    :** 2310040037 
**Date Submitted:** 21-03-2026

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `ga_knapsack.py` and read through it. Then answer these questions.

**Q1. What does the `fitness()` function return? Why does an overweight solution score 0?**

The fitness() function returns the total value of selected items if the total weight is within the allowed capacity. If the total weight exceeds the maximum limit, the function returns 0 as a penalty. This ensures that invalid overweight solutions are not selected by the algorithm.

**Q2. What does `tournament_select()` do? Why are higher-fitness individuals more likely to be chosen?**

tournament_select() randomly selects a small group of individuals and chooses the one with the highest fitness among them. This increases the chances of selecting better solutions while still maintaining diversity in the population.

**Q3. Look at the `run_ga()` loop. Find this line:**
```python
next_gen = [best_chromosome[:]]
```
**What is this doing? Why is it important to always keep the best solution?**

This line copies the best chromosome from the current generation into the next generation. This technique is called elitism and ensures that the best solution is not lost due to crossover or mutation, helping improve overall performance.

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python ga_knapsack.py
```

**Fill in this table:**

| Metric                             | Your result |
|------------------------------------|-------------|
| Number of generations              |     50      |
| Best value at generation 1         |     60      |
| Final best value                   |     77      |
| Total weight of best solution (kg) |     14.4    |
| Is solution valid (Yes / No)       |     Yes     |

**Copy the printed packing list here:**
+ Water bottle
+ First aid kit
+ Sleeping bag
+ Torch
+ Energy bars (x6)
+ Rain jacket
+ Map & compass
+ Cooking stove
+ Rope (10 m)
+ Sunscreen
+ Power bank

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest improvement happen? Does the curve flatten at some point?*

The fitness value increases very rapidly in the first few generations, jumping from 60 to around 75 within 2–3 generations. After that, the improvement becomes slower and stabilizes at 77. The curve clearly flattens after early generations, indicating fast convergence to a near-optimal solution.

## Experiment 2 — Effect of Mutation Rate

**Instructions:** In `ga_knapsack.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `mutation_rate` = **0.01**, **0.05**, and **0.30**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**

| mutation_rate | Final best value | Weight (kg) | Valid? | Shape of curve                         |
|---------------|------------------|-------------|--------|----------------------------------------|
| 0.01          | 75               | 14.9        | Yes    | Quick rise then long flat plateau      |
| 0.05          | 77               | 14.4        | Yes    | Fast rise then smooth stable plateau   |
| 0.30          | 78               | 14.1        | Yes    | Slight variations but still stabilizes |


**Compare the three plots. What happens when mutation is too low? Too high? (3–4 sentences)**  
*Hint: Too low = no diversity, may get stuck. Too high = random search. What is the sweet spot?*

For mutation rate 0.01, the graph rises quickly but gets stuck early at a lower value, showing lack of exploration. For 0.05, the graph rises quickly and stabilizes smoothly at a higher value, showing good balance. For 0.30, the graph still rises quickly but shows small variations before stabilizing at the highest value, indicating better exploration of the solution space.

**Which mutation_rate gave the best result? Why do you think that is?**

The mutation rate of 0.30 gave the best result because it allowed better exploration of different solutions and achieved the highest value of 78.

## Summary

**Complete this table with your best result from each experiment:**

| Experiment        | Key setting          | Final value | Main finding in one sentence                          |
|-------------------|----------------------|-------------|-------------------------------------------------------|
| 1 — Baseline      | mutation_rate = 0.05 | 77          | Fast convergence with stable solution                 |
| 2 — Mutation rate | mutation_rate = 0.30 | 78 | Higher mutation improved exploration and found better solution |


**In your own words — what is the most important thing you learned about Genetic Algorithms from these experiments? (3–5 sentences)**

Genetic Algorithms simulate natural evolution to find optimal solutions. From this experiment, I learned that mutation rate plays a key role in balancing exploration and convergence. Low mutation leads to early stagnation, while higher mutation improves exploration. In this case, a higher mutation rate helped achieve a better solution.

## Submission Checklist

- [ ] Student name and ID filled in
- [ ] Q1, Q2, Q3 answered
- [ ] Experiment 1: table filled, packing list pasted, plot observation written
- [ ] Experiment 2: results table filled (3 rows), observation and answer written
- [ ] Summary table completed and reflection written
- [ ] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
