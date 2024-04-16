# Scatter Search

## Name

Scatter Search, SS

## Taxonomy

Scatter Search is a population-based metaheuristic optimization algorithm that belongs to the field of Evolutionary Computation. It is closely related to other population-based metaheuristics such as Genetic Algorithms and Differential Evolution.

- Artificial Intelligence
  - Computational Intelligence
    - Evolutionary Computation
      - Evolutionary Algorithms
        - Genetic Algorithms
        - Differential Evolution
        - Scatter Search

## Strategy

### Diversification and Intensification

Scatter Search maintains a small population of diverse, high-quality solutions called the Reference Set. The algorithm balances exploration (diversification) and exploitation (intensification) by generating new solutions through combinations of the reference solutions and applying local search to improve them.

### Subset Generation and Combination

The Reference Set is divided into subsets, typically of size 2, and these subsets are used to generate new solutions through a combination method. The combination method aims to create offspring solutions that inherit desirable characteristics from their parents while introducing diversity.

### Improvement and Reference Set Update

Newly generated solutions undergo an improvement phase, usually through a local search procedure, to enhance their quality. The Reference Set is then updated by selectively replacing existing solutions with improved offspring solutions based on their fitness and diversity.

## Procedure

Data Structures:
- Reference Set: A small set of diverse, high-quality solutions
- Solution: A candidate solution to the optimization problem

Parameters:
- Reference Set Size: The number of solutions in the Reference Set
- Subset Size: The size of the subsets generated from the Reference Set for combination
- Maximum Iterations: The maximum number of iterations the algorithm will run

1. Initialization:
   1. Generate an initial population of solutions
   2. Evaluate the fitness of each solution
   3. Create the Reference Set by selecting a diverse set of high-quality solutions from the initial population

2. While stopping criteria are not met (e.g., maximum iterations):
   1. Subset Generation:
      1. Generate subsets of solutions from the Reference Set
   2. Combination:
      1. For each subset, apply a combination method to create new offspring solutions
   3. Improvement:
      1. Apply a local search procedure to improve the quality of the offspring solutions
   4. Reference Set Update:
      1. Evaluate the fitness of the improved offspring solutions
      2. Update the Reference Set by replacing low-quality solutions with high-quality, diverse offspring solutions
   5. Termination Check:
      1. Check if the stopping criteria are met (e.g., maximum iterations reached, satisfactory solution found)

3. Return the best solution found in the Reference Set

## Considerations

Advantages:
- Effective balance between exploration and exploitation
- Suitable for problems with complex, nonlinear search spaces
- Maintains a diverse set of high-quality solutions

Disadvantages:
- Requires the design of problem-specific combination and improvement methods
- May converge prematurely if the Reference Set loses diversity
- Can be computationally expensive due to the local search improvement phase

## Heuristics

### Reference Set Size

- Typically small, around 10-20 solutions
- Should be large enough to maintain diversity but small enough to keep computational costs reasonable

### Subset Size

- Usually set to 2 for pairwise combinations
- Can be increased for problems with high-dimensional search spaces or when more diverse combinations are desired

### Combination Method

- Should create offspring solutions that inherit desirable characteristics from parent solutions
- Common methods include linear combination, crossover operators (e.g., one-point, two-point, uniform), and path relinking

### Improvement Method

- Applies a local search procedure to enhance the quality of offspring solutions
- Can be problem-specific (e.g., hill climbing, simulated annealing) or general-purpose (e.g., pattern search, Nelder-Mead simplex)
- Balance the computational cost and the expected improvement in solution quality

### Diversity Management

- Maintain diversity in the Reference Set to prevent premature convergence
- Consider both fitness and diversity when updating the Reference Set
- Techniques such as crowding distance, fitness sharing, or clustering can be used to promote diversity

### Termination Criteria

- Set a maximum number of iterations based on computational budget and problem complexity
- Consider additional criteria such as the rate of improvement in solution quality or the diversity of the Reference Set
- Allow for early termination if a satisfactory solution is found

