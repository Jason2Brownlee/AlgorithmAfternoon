# Natural Evolution Strategy

## Name

Natural Evolution Strategy (NES)

## Taxonomy

Natural Evolution Strategy is a black-box optimization technique that belongs to the field of Evolutionary Computation, which is a subfield of Computational Intelligence. It is closely related to Evolution Strategies (ES) and Covariance Matrix Adaptation Evolution Strategy (CMA-ES).

- Computational Intelligence
  - Evolutionary Computation
    - Evolutionary Algorithms
      - Evolution Strategies
        - Covariance Matrix Adaptation Evolution Strategy (CMA-ES)
        - Natural Evolution Strategy (NES)

## Strategy

The Natural Evolution Strategy is inspired by the principles of natural evolution, where a population of candidate solutions is iteratively improved through a process of mutation and selection. The key idea behind NES is to parameterize the distribution of the mutation operator and adapt it based on the fitness landscape of the optimization problem.

### Mutation Distribution

In NES, the mutation operator is defined as a multivariate Gaussian distribution with a mean and a covariance matrix. The mean represents the current best solution, while the covariance matrix captures the dependencies between the variables and allows for adaptive exploration of the search space.

### Fitness Ranking

The fitness of each candidate solution is evaluated using the objective function of the optimization problem. The population is then ranked based on their fitness values, with better solutions receiving higher ranks.

### Distribution Update

The parameters of the mutation distribution (mean and covariance matrix) are updated based on the fitness ranking of the population. The update rule is derived using the natural gradient, which is a second-order optimization method that takes into account the geometry of the parameter space.

### Iterative Process

The above steps are repeated iteratively until a termination criterion is met, such as reaching a maximum number of iterations or achieving a satisfactory fitness value. The best solution found during the optimization process is returned as the final result.

## Procedure

### Data Structures

- Population: A set of candidate solutions, where each solution is represented as a real-valued vector.
- Fitness: An array storing the fitness value of each candidate solution.
- Mean: The mean vector of the mutation distribution.
- Covariance Matrix: A symmetric positive definite matrix representing the covariance of the mutation distribution.

### Parameters

- Population Size: The number of candidate solutions in each iteration.
- Learning Rate: A step size parameter that controls the magnitude of the distribution update.
- Initial Mean: The initial mean vector of the mutation distribution.
- Initial Covariance Matrix: The initial covariance matrix of the mutation distribution.
- Termination Criteria: Conditions for stopping the optimization process, such as maximum iterations or fitness threshold.

### Optimization Process

1. Initialize the population by sampling candidate solutions from the initial mutation distribution.
2. Evaluate the fitness of each candidate solution using the objective function.
3. Rank the population based on their fitness values.
4. Update the parameters of the mutation distribution (mean and covariance matrix) using the natural gradient and the fitness ranking.
5. Sample a new population from the updated mutation distribution.
6. Repeat steps 2-5 until the termination criteria are met.
7. Return the best solution found during the optimization process.

## Considerations

### Advantages

- Black-Box Optimization: NES does not require gradient information of the objective function, making it suitable for problems where the gradient is unavailable or difficult to compute.
- Adaptive Exploration: The covariance matrix adaptation allows NES to automatically adjust the exploration of the search space based on the fitness landscape, leading to efficient search in high-dimensional spaces.
- Invariance Properties: NES is invariant to rank-preserving transformations of the objective function and is also invariant to rotations and translations of the search space.

### Disadvantages

- Computational Complexity: The update of the covariance matrix in NES involves matrix operations, which can be computationally expensive, especially for high-dimensional problems.
- Parameter Sensitivity: The performance of NES can be sensitive to the choice of hyperparameters, such as the population size and learning rate, requiring careful tuning for optimal results.
- Local Optima: Like other evolutionary algorithms, NES can potentially get stuck in local optima, especially in multimodal landscapes with many suboptimal solutions.

## Heuristics

### Population Size

- The population size should be large enough to maintain diversity and prevent premature convergence, but not too large to avoid excessive computational overhead.
- A common heuristic is to set the population size proportional to the dimensionality of the problem, e.g., 4 + floor(3 * log(N)), where N is the number of variables.

### Learning Rate

- The learning rate controls the step size of the distribution update and balances exploration and exploitation.
- A small learning rate leads to slow convergence but more thorough exploration, while a large learning rate can lead to faster convergence but may miss the global optimum.
- The learning rate can be adapted during the optimization process, starting with a larger value for exploration and gradually decreasing it for fine-tuning.

### Initial Distribution

- The initial mean of the mutation distribution is usually set to a random point in the search space or a domain-specific starting point if prior knowledge is available.
- The initial covariance matrix is often set to the identity matrix multiplied by a scaling factor that reflects the expected scale of the variables.

### Termination Criteria

- The maximum number of iterations should be set based on the available computational budget and the complexity of the problem.
- A fitness threshold can be used to stop the optimization process when a satisfactory solution is found.
- Additional termination criteria can include monitoring the convergence rate, diversity of the population, or the change in the best fitness value over a certain number of iterations.

### Handling Constraints

- If the optimization problem has constraints, they can be handled by penalizing the fitness of infeasible solutions or by using repair mechanisms to project infeasible solutions onto the feasible region.
- Alternatively, the mutation operator can be designed to generate only feasible solutions by incorporating domain-specific knowledge or using constraint-handling techniques like resample or boundary handling.
