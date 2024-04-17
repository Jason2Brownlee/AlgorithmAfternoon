# Composite Differential Evolution

## Name

Composite Differential Evolution (CoDE)

## Taxonomy

Composite Differential Evolution is a population-based stochastic optimization algorithm that belongs to the field of Evolutionary Computation, which is a subfield of Computational Intelligence. It is an extension of the classic Differential Evolution (DE) algorithm.

- Computational Intelligence
  - Biologically Inspired Computation
    - Evolutionary Computation
      - Evolutionary Algorithms
        - Differential Evolution (DE)
          - Composite Differential Evolution (CoDE)

## Strategy

Composite Differential Evolution combines three trial vector generation strategies and three control parameter settings from the classic Differential Evolution algorithm. The strategy randomly selects one of the three trial vector generation methods and one of the three control parameter settings to create a new trial vector for each individual in the population. This approach allows the algorithm to adapt to the characteristics of the problem being solved, as different strategies and parameter settings may be more effective at different stages of the optimization process.

The three trial vector generation strategies used in CoDE are:

1. DE/rand/1/bin: The trial vector is created by adding the weighted difference between two randomly selected individuals to a third randomly selected individual. The binomial crossover operator is then applied to combine the trial vector with the target vector.

2. DE/rand/2/bin: Similar to DE/rand/1/bin, but the trial vector is created by adding the weighted differences between two pairs of randomly selected individuals.

3. DE/current-to-rand/1: The trial vector is created by adding the weighted difference between a randomly selected individual and the target vector to another randomly selected individual. A binary crossover operator is then applied to combine the trial vector with the target vector.

The three control parameter settings used in CoDE are:

1. F = 1.0, Cr = 0.1
2. F = 1.0, Cr = 0.9
3. F = 0.8, Cr = 0.2

where F is the scaling factor and Cr is the crossover rate.

## Procedure

### Data Structures

- Population: An array of candidate solutions, where each solution is a vector of real numbers.
- Trial Vector: A new candidate solution generated by applying a trial vector generation strategy and control parameter settings to individuals in the population.
- Target Vector: The current candidate solution that is being compared to the trial vector.
- Best Solution: The candidate solution with the best fitness value found so far during the optimization process.

### Parameters

- Population Size (NP): The number of candidate solutions in the population.
- Scaling Factor (F): A parameter that controls the magnitude of the differential mutation operator.
- Crossover Rate (Cr): A parameter that determines the probability of each component of the trial vector being inherited from the mutant vector.
- Max Generations: The maximum number of iterations the algorithm will run before terminating.

### Pseudocode

1. Initialize the population with NP candidate solutions
2. Evaluate the fitness of each candidate solution in the population
3. While the termination criterion is not met (e.g., max generations):
   1. For each candidate solution (target vector) in the population:
      1. Select a trial vector generation strategy and control parameter settings
      2. Generate a mutant vector using the selected strategy and parameters
      3. Create a trial vector by applying the binomial crossover operator to the mutant vector and the target vector
      4. Evaluate the fitness of the trial vector
      5. If the trial vector has better fitness than the target vector, replace the target vector with the trial vector
   2. Update the best solution found so far
4. Return the best solution found

## Considerations

### Advantages

- Adaptability: CoDE can adapt to the characteristics of the problem being solved by using different trial vector generation strategies and control parameter settings.
- Robustness: The combination of multiple strategies and parameter settings makes CoDE more robust to the choice of control parameters compared to classic DE.
- Efficiency: CoDE can often find better solutions in fewer iterations compared to classic DE, as it can quickly identify and exploit promising regions of the search space.

### Disadvantages

- Increased complexity: The use of multiple trial vector generation strategies and control parameter settings makes CoDE more complex to implement and understand compared to classic DE.
- Higher computational cost per iteration: CoDE requires more computations per iteration due to the need to generate and evaluate multiple trial vectors for each target vector.
- Parameter sensitivity: While CoDE is more robust to parameter settings than classic DE, the performance of the algorithm can still be sensitive to the choice of population size, scaling factor, and crossover rate.

## Heuristics

### Population Size

- The population size should be large enough to maintain diversity and avoid premature convergence, but not so large that the computational cost becomes prohibitive.
- A common heuristic is to set the population size to 10 times the dimensionality of the problem, but this may need to be adjusted based on the complexity of the problem.

### Scaling Factor

- The scaling factor controls the magnitude of the differential mutation operator and should be set based on the characteristics of the problem.
- For problems with a larger search space or more complex fitness landscape, a larger scaling factor (e.g., F = 0.8 or 1.0) may be more effective.
- For problems with a smaller search space or simpler fitness landscape, a smaller scaling factor (e.g., F = 0.5) may be sufficient.

### Crossover Rate

- The crossover rate determines the probability of each component of the trial vector being inherited from the mutant vector and should be set based on the desired balance between exploration and exploitation.
- A higher crossover rate (e.g., Cr = 0.9) favors exploitation of the current best solutions, while a lower crossover rate (e.g., Cr = 0.1) favors exploration of new regions of the search space.
- A common heuristic is to set the crossover rate to a value between 0.1 and 0.9, depending on the characteristics of the problem.

### Termination Criterion

- The maximum number of generations should be set based on the available computational resources and the desired solution quality.
- For problems with a known optimal solution, the algorithm can be terminated when the best solution found is within a certain tolerance of the optimal solution.
- For problems with an unknown optimal solution, the algorithm can be terminated when the improvement in the best solution found over a certain number of generations falls below a specified threshold.
