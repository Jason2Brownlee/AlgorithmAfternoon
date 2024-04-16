# Univariate Marginal Distribution Algorithm

## Name

Univariate Marginal Distribution Algorithm (UMDA)

## Taxonomy

The Univariate Marginal Distribution Algorithm is a probabilistic model-building evolutionary algorithm that belongs to the field of Estimation of Distribution Algorithms (EDAs). It is closely related to other EDAs such as the Population-Based Incremental Learning (PBIL) algorithm and the Compact Genetic Algorithm (cGA).

- Computational Intelligence
  - Biologically Inspired Computation
    - Evolutionary Computation
      - Estimation of Distribution Algorithms
        - Univariate Marginal Distribution Algorithm

## Strategy

The UMDA maintains a probability vector that represents the distribution of promising solutions in the search space. This probability vector is used to generate new candidate solutions by sampling from the learned distribution. The algorithm starts with a uniform probability distribution, assuming equal likelihood for all possible values of each variable. As the search progresses, the probability vector is updated based on the best-performing solutions in each generation.

The key information processing steps in UMDA are:

### Probabilistic Modeling

UMDA estimates the probability distribution of the best solutions in each generation. It assumes independence between the variables and models the marginal probability distribution of each variable separately. This simplification allows for efficient learning and sampling of the probability distribution.

### Sampling

New candidate solutions are generated by sampling from the learned probability distribution. Each variable of a new solution is independently sampled according to its corresponding marginal probability. This process creates offspring that inherit the characteristics of the best-performing individuals in the previous generation.

### Selection

A selection mechanism, such as truncation selection, is applied to the combined population of parent and offspring solutions. The best-performing individuals are selected to update the probability vector for the next generation. This selection pressure drives the search towards promising regions of the search space.

## Procedure

1. Initialize the probability vector with a uniform distribution
   1.1. Set the probability of each variable to 1/K, where K is the number of possible values for that variable
2. Generate an initial population of N individuals by sampling from the probability vector
3. While the termination criterion is not met, repeat:
   3.1. Evaluate the fitness of each individual in the population
   3.2. Select the M best individuals based on their fitness
   3.3. Update the probability vector based on the selected individuals
       3.3.1. For each variable, calculate the frequency of each value among the selected individuals
       3.3.2. Set the probability of each value to its corresponding frequency
   3.4. Generate N new individuals by sampling from the updated probability vector
   3.5. Replace the current population with the new individuals
4. Return the best solution found

### Data Structures

- Probability Vector: A vector of length L, where L is the number of variables in the problem. Each element of the vector represents the marginal probability distribution of a specific variable.
- Population: An array of N individuals, where each individual is represented as a vector of L variables.

### Parameters

- N: Population size
- M: Number of selected individuals for updating the probability vector
- K: Number of possible values for each variable
- Termination Criterion: Condition for stopping the algorithm, such as a maximum number of generations or a target fitness value

## Considerations

### Advantages

- Simplicity: UMDA is conceptually simple and easy to implement compared to other EDAs and evolutionary algorithms.
- Efficiency: By assuming independence between variables, UMDA can learn and sample from the probability distribution efficiently, even for high-dimensional problems.
- Adaptability: UMDA can adapt to different problem domains by modifying the representation of the probability vector and the sampling mechanism.

### Disadvantages

- Limited Expressiveness: The assumption of independence between variables may not hold for all problems, limiting the algorithm's ability to capture complex variable interactions.
- Premature Convergence: UMDA may suffer from premature convergence if the probability vector becomes too focused on a suboptimal solution, reducing exploration of the search space.
- Parameter Sensitivity: The performance of UMDA can be sensitive to the choice of population size (N) and the number of selected individuals (M). Careful tuning of these parameters is often required for optimal results.

## Heuristics

### Population Size (N)

- Start with a population size that is at least 10 times the number of variables in the problem.
- Increase the population size for more complex problems or when dealing with high-dimensional search spaces.
- Consider the balance between exploration and exploitation when setting the population size. Larger populations promote exploration, while smaller populations encourage exploitation.

### Selection Pressure (M)

- The number of selected individuals (M) controls the selection pressure in UMDA. Higher values of M result in stronger selection pressure, focusing the search on the best-performing regions.
- A common heuristic is to set M to be around 50% of the population size (N). This provides a balance between exploiting good solutions and maintaining diversity.
- Adjust the selection pressure based on the problem characteristics. For problems with many local optima, a lower selection pressure can help maintain diversity and avoid premature convergence.

### Termination Criterion

- Set a maximum number of generations based on the available computational resources and the problem complexity. This prevents the algorithm from running indefinitely.
- Define a target fitness value or a convergence threshold based on the desired solution quality. The algorithm can terminate when the best fitness reaches or exceeds this value.
- Implement early stopping mechanisms to detect and terminate the algorithm if the population becomes stagnant or if the fitness improvement becomes negligible over a certain number of generations.

### Probability Vector Initialization

- Initialize the probability vector with a uniform distribution to provide equal chances for all possible variable values in the beginning.
- If prior knowledge about the problem is available, the initial probabilities can be biased towards promising regions of the search space.
- Avoid setting the initial probabilities to extreme values (0 or 1) unless there is strong evidence to support such a bias.

### Handling Constrained Problems

- Incorporate constraint handling techniques, such as penalty functions or repair mechanisms, to deal with constraints in the problem domain.
- Modify the sampling process to ensure that the generated solutions satisfy the constraints.
- Adjust the fitness evaluation to consider the feasibility of solutions and guide the search towards feasible regions of the search space.