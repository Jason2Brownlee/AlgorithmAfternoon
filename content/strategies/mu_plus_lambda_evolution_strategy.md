---
title: (μ+λ)-Evolution Strategy
---
# (μ+λ)-Evolution Strategy

## Name

(μ+λ)-Evolution Strategy, (mu+lambda)-ES, (μ+λ)-ES

## Taxonomy

The (μ+λ)-Evolution Strategy is a population-based, stochastic optimization algorithm that belongs to the field of Evolutionary Computation, a subfield of Computational Intelligence.

- Computational Intelligence
  - Evolutionary Computation
    - Evolutionary Algorithms
      - Evolution Strategies
        - (μ+λ)-Evolution Strategy

## Strategy

The (μ+λ)-Evolution Strategy maintains a population of μ candidate solutions, known as parents. In each iteration, the algorithm generates λ new candidate solutions, called offspring, by applying mutation to the parents. The mutation operator typically adds random perturbations to the parent solutions, enabling the algorithm to explore the search space. The degree of perturbation is controlled by a set of strategy parameters, which are often adapted during the optimization process to balance exploration and exploitation.

After generating the offspring, the (μ+λ)-ES selects the best μ individuals from the combined pool of parents and offspring to form the population for the next iteration. This selection mechanism ensures that the best solutions found so far are always preserved, leading to an elitist strategy that emphasizes exploitation of promising regions in the search space.

The process of mutation and selection continues iteratively until a predefined termination criterion is met, such as reaching a maximum number of iterations or finding a solution of satisfactory quality. The (μ+λ)-ES is known for its ability to handle continuous optimization problems and adapt to the problem landscape through the self-adaptation of strategy parameters.

## Procedure

### Data Structures

- Population: An array of μ candidate solutions, each represented as a real-valued vector.
- Strategy Parameters: A set of parameters that control the mutation operator, typically including the mutation strength (step size) for each dimension of the solution vector.

### Parameters

- μ: The number of parent solutions in the population.
- λ: The number of offspring generated in each iteration.
- Termination Criterion: A condition that determines when the algorithm should stop, such as a maximum number of iterations or a target fitness value.

### Pseudocode

1. Initialize the population with μ randomly generated candidate solutions.
2. Initialize the strategy parameters for each candidate solution.
3. While the termination criterion is not met, do:
   1. For each of the λ offspring, do:
      1. Select a parent solution uniformly at random from the population.
      2. Create a new offspring by applying mutation to the selected parent using the associated strategy parameters.
   2. Evaluate the fitness of each offspring solution.
   3. Select the best μ individuals from the combined pool of parents and offspring to form the new population.
   4. Update the strategy parameters of the selected individuals based on their performance.
4. Return the best solution found.

## Considerations

### Advantages

- Effective in handling continuous optimization problems.
- Self-adaptation of strategy parameters allows the algorithm to adapt to the problem landscape.
- Elitist selection ensures that the best solutions found so far are preserved.

### Disadvantages

- Performance may deteriorate in high-dimensional search spaces.
- The algorithm may converge prematurely if the population diversity is not maintained.
- The choice of μ and λ can significantly impact the performance and needs to be tuned for each problem.

## Heuristics

### Population Size

- The ratio of μ to λ should be chosen based on the problem characteristics. A common rule of thumb is to set μ ≈ λ/7.
- Larger population sizes can improve exploration but increase computational cost.

### Mutation Strength

- The initial mutation strength should be set based on the expected scale of the problem variables.
- Mutation strength should be adapted during the optimization process to maintain a balance between exploration and exploitation.

### Termination Criterion

- The maximum number of iterations should be set based on the available computational resources and the problem complexity.
- An alternative termination criterion can be based on the rate of improvement in the best fitness value over a fixed number of iterations.

### Strategy Parameter Adaptation

- The 1/5-success rule is a common heuristic for adapting the mutation strength: If more than 20% of the offspring are successful (i.e., better than their parents), increase the mutation strength; otherwise, decrease it.
- More advanced adaptation mechanisms, such as self-adaptation or covariance matrix adaptation, can be employed to improve the algorithm's performance.
