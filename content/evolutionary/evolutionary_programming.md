# Evolutionary Programming

## Name

Evolutionary Programming (EP)

## Taxonomy

Evolutionary Programming is a biologically inspired optimization technique that falls under the broader category of Evolutionary Computation, which is a subfield of Computational Intelligence. It is closely related to other evolutionary algorithms such as Genetic Algorithms and Evolution Strategies.

- Computational Intelligence
  - Biologically Inspired Computation
    - Evolutionary Computation
      - Evolutionary Programming

## Strategy

Evolutionary Programming is a population-based optimization technique that draws inspiration from the principles of biological evolution. The algorithm maintains a population of candidate solutions, each representing a potential solution to the problem at hand. These candidate solutions are iteratively evolved through a process of mutation and selection, with the aim of improving their fitness or quality over successive generations.

### Representation

In EP, each candidate solution is typically represented as a fixed-length vector of real-valued numbers or a set of parameters that define the solution. The specific representation depends on the nature of the problem being solved.

### Mutation

The primary variation operator in EP is mutation. During each generation, each candidate solution undergoes a mutation process, where its parameters are slightly modified according to a predefined mutation strategy. The mutation strategy is designed to introduce small, random perturbations to the solution, allowing it to explore the search space.

### Evaluation and Selection

After the mutation phase, each candidate solution is evaluated using a fitness function that measures its quality or performance with respect to the problem objective. The fitness function assigns a fitness value to each solution, indicating its relative merit.

Based on the fitness values, a selection process is applied to determine which candidate solutions will survive to the next generation. The selection mechanism typically favors solutions with higher fitness values, promoting the survival and reproduction of better-performing individuals.

### Iteration

The process of mutation, evaluation, and selection is repeated for a predefined number of generations or until a termination criterion is met. As the generations progress, the population is expected to evolve and converge towards better solutions.

## Procedure

1. Initialize the population:
   1. Determine the population size and the representation of candidate solutions.
   2. Randomly initialize each candidate solution in the population.

2. Evaluate the initial population:
   1. For each candidate solution, calculate its fitness value using the fitness function.

3. Repeat for a specified number of generations or until a termination criterion is met:
   1. Mutation:
      1. For each candidate solution in the population:
         1. Apply the mutation strategy to create a new offspring solution.
         2. Evaluate the fitness of the offspring solution.
   2. Selection:
      1. Select the surviving individuals from the current population and their offspring based on their fitness values.
      2. Create a new population by replacing the current population with the selected individuals.

4. Return the best solution found during the evolutionary process.

### Data Structures

- Population: An array or list of candidate solutions.
- Candidate Solution: A fixed-length vector of real-valued numbers or a set of parameters representing a potential solution.
- Fitness Value: A scalar value indicating the quality or performance of a candidate solution.

### Parameters

- Population Size: The number of candidate solutions in the population.
- Number of Generations: The maximum number of iterations or generations allowed.
- Mutation Strategy: The method used to mutate the candidate solutions, such as Gaussian mutation or Cauchy mutation.
- Selection Mechanism: The strategy used to select surviving individuals, such as tournament selection or truncation selection.

## Considerations

### Advantages

- Simplicity: EP has a relatively simple and straightforward implementation compared to other evolutionary algorithms.
- Flexibility: EP can be easily adapted to various problem domains and can handle both continuous and discrete optimization problems.
- Robustness: EP is known for its ability to escape local optima and explore the search space effectively.

### Disadvantages

- Parameter Sensitivity: The performance of EP can be sensitive to the choice of mutation strategy and its associated parameters.
- Convergence Speed: EP may have slower convergence compared to some other optimization algorithms, especially for high-dimensional problems.
- Lack of Crossover: Unlike Genetic Algorithms, EP does not typically employ a crossover operator, which can limit the exploration of the search space.

## Heuristics

### Population Size

- Start with a population size that is at least 10 times the dimensionality of the problem.
- Increase the population size for more complex or high-dimensional problems to ensure adequate exploration of the search space.

### Mutation Strategy

- Use Gaussian mutation as a starting point, as it is a commonly used and effective mutation strategy.
- Experiment with different mutation strategies, such as Cauchy mutation or self-adaptive mutation, to see if they improve performance for the specific problem.
- Adjust the mutation step size or variance based on the scale and characteristics of the problem.

### Selection Mechanism

- Tournament selection is a popular choice for EP due to its simplicity and effectiveness.
- Consider using truncation selection for problems with a large population size, as it can be computationally more efficient.
- Experiment with different selection pressures (e.g., tournament size) to balance exploration and exploitation.

### Termination Criteria

- Set a maximum number of generations based on the available computational resources and the complexity of the problem.
- Monitor the progress of the best fitness value over generations and consider terminating if no significant improvement is observed for a certain number of generations.
- Implement additional termination criteria based on problem-specific requirements, such as reaching a target fitness value or a maximum allowed runtime.
