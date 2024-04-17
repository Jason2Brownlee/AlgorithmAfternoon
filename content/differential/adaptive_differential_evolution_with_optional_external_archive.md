# Adaptive Differential Evolution with Optional External Archive

## Name

Adaptive Differential Evolution with Optional External Archive (JADE)

## Taxonomy

Adaptive Differential Evolution with Optional External Archive (JADE) is a stochastic optimization algorithm that belongs to the field of Evolutionary Computation, a subfield of Computational Intelligence. It is an extension of the classic Differential Evolution (DE) algorithm.

- Computational Intelligence
  - Evolutionary Computation
    - Evolutionary Algorithms
      - Differential Evolution (DE)
        - Adaptive Differential Evolution with Optional External Archive (JADE)

## Strategy

### Mutation and Crossover

JADE introduces a new mutation strategy called "DE/current-to-pbest" which creates a mutant vector by combining the current individual, the best individual from a subset of the population, and a randomly selected individual. The crossover operation is performed between the current individual and the mutant vector to create a trial vector.

### Parameter Adaptation

JADE adapts the mutation factor (F) and crossover rate (CR) for each individual based on the successful values of these parameters in the previous generation. This adaptation allows the algorithm to automatically adjust to the characteristics of the problem being solved.

### Optional External Archive

JADE maintains an optional external archive of previously successful individuals. This archive is used in the mutation strategy to provide additional diversity and to help the algorithm escape local optima.

## Procedure

### Data Structures

- Population: An array of individuals, where each individual represents a candidate solution to the optimization problem.
- Archive: An optional external archive that stores previously successful individuals.

### Parameters

- NP: Population size
- F: Mutation factor
- CR: Crossover rate
- p: Greediness of the mutation strategy (proportion of top individuals used in mutation)
- c: Rate of parameter adaptation

### Steps

1. Initialize the population with NP individuals randomly distributed in the search space.
2. Initialize the mutation factor (F) and crossover rate (CR) for each individual.
3. Evaluate the fitness of each individual in the population.
4. For each individual (target vector) in the population:
   1. Select the best individual from a randomly chosen subset of the population (pbest).
   2. Select two random individuals from the population or the archive.
   3. Create a mutant vector using the "DE/current-to-pbest" strategy.
   4. Perform crossover between the target vector and the mutant vector to create a trial vector.
   5. Evaluate the fitness of the trial vector.
   6. If the trial vector has better fitness than the target vector, replace the target vector with the trial vector in the population.
   7. If the trial vector replaces the target vector, add the replaced target vector to the archive (if using an archive).
   8. Update the mutation factor (F) and crossover rate (CR) of the individual based on the success of the trial vector.
5. If the maximum number of generations or the termination condition is not met, go to step 4.
6. Return the best individual found in the population as the solution.

## Considerations

### Advantages

- Adaptive parameter control: JADE automatically adapts the mutation factor and crossover rate for each individual, making it more robust and reducing the need for manual parameter tuning.
- Improved convergence: The "DE/current-to-pbest" mutation strategy and the optional external archive help JADE converge faster and find better solutions compared to classic DE.
- Robustness: JADE is less sensitive to the initial parameter settings and can adapt to a wide range of optimization problems.

### Disadvantages

- Increased complexity: The adaptive parameter control and optional external archive add complexity to the algorithm, making it more difficult to implement and understand compared to classic DE.
- Memory overhead: If using an external archive, JADE requires additional memory to store the previously successful individuals.
- Sensitivity to greediness parameter: The performance of JADE can be sensitive to the setting of the greediness parameter (p), which controls the balance between exploitation and exploration.

## Heuristics

### Population Size (NP)

- As a general rule, set the population size (NP) to be 5 to 10 times the dimensionality of the problem.
- For high-dimensional problems (100 or more dimensions), consider using a smaller population size to reduce computational overhead.
- If the population size is too small, the algorithm may converge prematurely or struggle to find good solutions.

### Greediness Parameter (p)

- The greediness parameter (p) controls the balance between exploitation and exploration in the mutation strategy.
- A smaller value of p (e.g., 0.05) favors exploitation, while a larger value (e.g., 0.5) favors exploration.
- For unimodal problems or problems with few local optima, use a smaller value of p to focus on exploitation.
- For multimodal problems or problems with many local optima, use a larger value of p to maintain diversity and explore the search space more thoroughly.

### External Archive

- Using an external archive can improve the performance of JADE, especially for problems with many local optima.
- The size of the archive should be related to the population size. A common choice is to set the archive size equal to the population size.
- If memory is limited or the problem is relatively simple, consider not using an archive to reduce the computational overhead.

### Parameter Adaptation

- The rate of parameter adaptation (c) controls how quickly the mutation factor and crossover rate are updated based on their success in the previous generation.
- A smaller value of c (e.g., 0.1) results in slower adaptation, while a larger value (e.g., 0.9) results in faster adaptation.
- For problems with rapidly changing landscapes or noisy fitness functions, use a smaller value of c to avoid premature convergence.
- For problems with smooth landscapes or when quick convergence is desired, use a larger value of c to adapt the parameters more quickly.
