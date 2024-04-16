# Evolution Strategies

## Name

Evolution Strategies (ES), Evolutionary Strategies

## Taxonomy

Evolution Strategies are a class of optimization algorithms that belong to the field of Evolutionary Computation, which is a subfield of Computational Intelligence. They are closely related to other Evolutionary Algorithms such as Genetic Algorithms, Evolutionary Programming, and Genetic Programming.

- Computational Intelligence
  - Evolutionary Computation
    - Evolutionary Algorithms
      - Genetic Algorithms
      - Evolutionary Programming
      - Evolution Strategies
      - Genetic Programming

## Strategy

Evolution Strategies are inspired by the principles of biological evolution, particularly the process of natural selection and the concept of survival of the fittest. The algorithm maintains a population of candidate solutions, each represented by a vector of real-valued parameters. These candidate solutions are referred to as individuals or offspring.

The algorithm iteratively modifies the population of candidate solutions through a series of genetic operators, namely mutation and recombination (also known as crossover). Mutation introduces random variations into the individuals, while recombination combines genetic information from multiple parents to create new offspring.

The fitness of each individual is evaluated using an objective function, which measures the quality or performance of the candidate solution in the context of the optimization problem. The goal is to find the individual with the highest fitness value, representing the optimal or near-optimal solution to the problem.

Selection mechanisms are employed to determine which individuals from the current population will survive and contribute to the next generation. The selection process favors individuals with higher fitness values, allowing them to pass on their genetic information to future generations.

The algorithm continues to iteratively apply the genetic operators, evaluate fitness, and perform selection until a termination criterion is met. This criterion can be a predefined number of generations, a satisfactory fitness level, or a convergence threshold.

## Procedure

1. Initialize the population:
   1. Determine the population size (μ) and the number of offspring (λ).
   2. Create an initial population of μ individuals, each represented by a vector of real-valued parameters.
   3. Evaluate the fitness of each individual in the initial population using the objective function.

2. While the termination criterion is not met, repeat the following steps:
   1. Recombination:
      1. Select ρ parent individuals from the current population based on their fitness.
      2. Create λ new offspring by applying recombination operators (e.g., intermediate recombination, discrete recombination) to the selected parents.
   2. Mutation:
      1. For each offspring created in the recombination step, apply mutation operators (e.g., Gaussian mutation) to introduce random variations.
      2. Adjust the mutation strength (step size) based on the selected mutation strategy (e.g., 1/5th rule, self-adaptation).
   3. Fitness evaluation:
      1. Evaluate the fitness of each offspring using the objective function.
   4. Selection:
      1. Select μ individuals from the combined population of parents and offspring based on their fitness.
      2. The selected individuals form the population for the next generation.

3. Return the best individual found during the optimization process as the solution.

### Data Structures and Parameters

- Population: An array or list of individuals, where each individual is represented by a vector of real-valued parameters.
- Fitness values: An array or list storing the fitness value of each individual in the population.
- Population size (μ): The number of individuals in the population.
- Offspring size (λ): The number of offspring created in each generation.
- Recombination size (ρ): The number of parents selected for recombination.
- Mutation strength (step size): A parameter controlling the magnitude of mutations applied to the offspring.
- Termination criterion: A condition that determines when to stop the optimization process (e.g., maximum number of generations, fitness threshold).

## Considerations

### Advantages

- Suitable for continuous optimization problems with real-valued parameters.
- Can effectively explore and exploit the search space, balancing global and local search.
- Robust to noise and can handle non-differentiable and non-convex objective functions.
- Parallelizable, allowing for efficient utilization of computational resources.

### Disadvantages

- May require a large number of fitness evaluations, which can be computationally expensive.
- The choice of mutation strength and other strategy parameters can significantly impact the algorithm's performance.
- May converge prematurely to suboptimal solutions if the population diversity is not maintained.

## Heuristics

### Population Sizing

- A larger population size (μ) can improve the exploration of the search space but may increase computational costs.
- The offspring size (λ) is typically larger than the population size (μ) to promote diversity and exploration.
- A common setting is to have λ = 7μ, but this can be adjusted based on the problem characteristics.

### Recombination

- Intermediate recombination is a common choice, where the offspring parameters are calculated as the weighted average of the parent parameters.
- Discrete recombination can also be used, where each offspring parameter is randomly selected from one of the parents.
- The recombination size (ρ) is often set to 2 for intermediate recombination and higher values for discrete recombination.

### Mutation

- Gaussian mutation is commonly employed, where random values drawn from a Gaussian distribution are added to the offspring parameters.
- The mutation strength (step size) should be adapted during the optimization process to balance exploration and exploitation.
- The 1/5th rule is a simple adaptation strategy that adjusts the mutation strength based on the success rate of mutations in the previous generations.
- Self-adaptation strategies, such as the log-normal self-adaptation, allow the mutation strengths to evolve along with the candidate solutions.

### Termination Criteria

- A maximum number of generations or function evaluations can be specified to limit the computational resources used.
- A fitness threshold can be set, and the algorithm can be terminated when an individual achieves a fitness value above the threshold.
- Convergence criteria, such as the difference in fitness between the best and worst individuals or the rate of improvement, can be used to detect stagnation and terminate the algorithm.

