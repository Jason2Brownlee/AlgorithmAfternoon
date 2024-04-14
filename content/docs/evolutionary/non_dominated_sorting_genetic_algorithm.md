# Non-dominated Sorting Genetic Algorithm

## Name

Non-dominated Sorting Genetic Algorithm (NSGA), NSGA-II, Multi-Objective Genetic Algorithm (MOGA)

## Taxonomy

NSGA is a multi-objective optimization algorithm that belongs to the field of Evolutionary Computation, a subfield of Computational Intelligence. It is closely related to other multi-objective evolutionary algorithms such as SPEA, PAES, and MOEA/D.

- Computational Intelligence
  - Evolutionary Computation
    - Multi-Objective Optimization
      - Non-dominated Sorting Genetic Algorithm (NSGA)

## Strategy

NSGA is a population-based metaheuristic that maintains a set of candidate solutions and iteratively improves them through selection, crossover, and mutation operations. The key feature of NSGA is its use of non-dominated sorting to rank solutions based on their Pareto optimality.

### Non-dominated Sorting

In each generation, NSGA sorts the population into different fronts based on the dominance relationship between solutions. A solution is said to dominate another if it is better in at least one objective and not worse in any other objectives. The first front contains all non-dominated solutions, the second front contains solutions dominated only by those in the first front, and so on.

### Crowding Distance

To maintain diversity among solutions, NSGA also calculates the crowding distance for each solution within its front. Crowding distance measures the density of solutions surrounding a particular solution in the objective space. Solutions with higher crowding distances are preferred to prevent clustering and promote a well-spread Pareto front.

### Selection and Reproduction

NSGA uses binary tournament selection to choose parents for reproduction. The selection process considers both the non-domination rank and crowding distance, favoring solutions from better fronts and those with higher crowding distances within the same front. The selected parents undergo crossover and mutation to create offspring, which are then combined with the current population for the next round of non-dominated sorting.

## Procedure

Data Structures:
- Population: A set of candidate solutions
- Front: A subset of the population containing non-dominated solutions
- Crowding Distance: A measure of the density of solutions surrounding a particular solution

Parameters:
- Population Size: The number of solutions in the population
- Crossover Probability: The probability of performing crossover between two parent solutions
- Mutation Probability: The probability of mutating a solution
- Maximum Generations: The stopping criterion for the algorithm

Steps:
1. Initialize the population with random solutions
2. Evaluate the objective values for each solution
3. Perform non-dominated sorting on the population
   1. Create an empty set of fronts
   2. Find all non-dominated solutions and add them to the first front
   3. Remove the first front from the population
   4. Repeat steps 3.2 and 3.3 until all solutions are assigned to a front
4. Calculate crowding distances for solutions within each front
5. Select parents using binary tournament selection
   1. Choose two random solutions from the population
   2. Select the solution with the better (lower) front rank
   3. If both solutions are from the same front, select the one with higher crowding distance
6. Create offspring through crossover and mutation
7. Combine the current population with the offspring
8. Repeat steps 3-7 until the maximum number of generations is reached
9. Return the set of non-dominated solutions (first front) as the Pareto optimal set

## Considerations

Advantages:
- Maintains a diverse set of solutions along the Pareto front
- Suitable for problems with multiple conflicting objectives
- Does not require prior knowledge of the problem structure or objectives

Disadvantages:
- Computational complexity increases with the number of objectives and population size
- May struggle with problems having a large number of objectives (more than 3-4)
- The performance depends on the choice of genetic operators and parameter values

## Heuristics

### Population Size
- A larger population size can improve the exploration of the search space but increases computational cost
- Typically set between 50-200 depending on the problem complexity

### Crossover and Mutation Probabilities
- Higher crossover probability (0.8-0.9) promotes exploitation of good solutions
- Lower mutation probability (0.01-0.1) helps maintain diversity and escape local optima
- Balance the two based on the desired exploration-exploitation trade-off

### Genetic Operators
- Choose crossover and mutation operators suitable for the solution representation (e.g., binary, real-valued)
- Experiment with different operators and their variants to find the best performing combination

### Stopping Criterion
- Set the maximum number of generations based on the available computational resources and time constraints
- Monitor the convergence of the Pareto front and stop if no significant improvement is observed over a certain number of generations

### Problem-specific Modifications
- Incorporate domain knowledge and problem-specific heuristics to improve the search efficiency
- Customize the genetic operators, selection scheme, or solution representation based on the characteristics of the problem at hand
