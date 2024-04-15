---
title: (μ,λ)-Evolution Strategy
---
# (μ,λ)-Evolution Strategy

## Name

(μ,λ)-Evolution Strategy, (μ,λ)-ES, (mu,lambda)-Evolution Strategy, (mu,lambda)-ES

## Taxonomy

The (μ,λ)-Evolution Strategy is a population-based stochastic optimization algorithm belonging to the field of Evolutionary Computation, a subfield of Computational Intelligence. It is closely related to other Evolution Strategies, such as (1+1)-ES and (μ+λ)-ES.

- Computational Intelligence
  - Evolutionary Computation
    - Evolutionary Algorithms
      - Evolution Strategies
        - (1+1)-Evolution Strategy
        - (μ+λ)-Evolution Strategy
        - (μ,λ)-Evolution Strategy

## Strategy

### Population-Based Search

The (μ,λ)-Evolution Strategy maintains a population of μ candidate solutions, called parents. In each iteration, the algorithm generates λ new candidate solutions, called offspring, by applying mutation to the parents. The mutation operator typically adds random perturbations drawn from a normal distribution to the parent solutions.

### Selection

After generating the offspring, the (μ,λ)-ES selects the μ best solutions from the λ offspring to form the parent population for the next iteration. This selection mechanism is called comma-selection, as it only considers the offspring for selection, and not the parents from the previous iteration.

### Adaptive Mutation

The (μ,λ)-ES often employs an adaptive mutation mechanism, where the parameters of the mutation operator, such as the step size or the covariance matrix, are adapted during the search process. This allows the algorithm to automatically adjust the search behavior based on the characteristics of the optimization problem.

## Procedure

Data Structures:
- Population: An array of μ candidate solutions, each represented as a real-valued vector.
- Fitness: An array of μ fitness values, corresponding to the candidate solutions in the population.

Parameters:
- μ: The number of parent solutions.
- λ: The number of offspring solutions generated in each iteration.
- maxIterations: The maximum number of iterations.
- mutationStepSize: The initial step size for the mutation operator.

Steps:
1. Initialize the population with μ randomly generated candidate solutions.
2. Evaluate the fitness of each candidate solution in the population.
3. Repeat until the termination criterion is met (e.g., maximum iterations):
   1. Generate λ offspring solutions by applying mutation to the parent solutions:
      1. For each offspring:
         1. Select a parent solution uniformly at random.
         2. Create a new solution by adding random perturbations to the parent solution, using the mutation step size.
   2. Evaluate the fitness of each offspring solution.
   3. Select the μ best solutions from the λ offspring to form the new parent population.
   4. Update the mutation step size based on the success rate of the offspring solutions.
4. Return the best solution found during the search.

## Considerations

Advantages:
- Effective for solving continuous optimization problems.
- Requires minimal assumptions about the problem structure.
- Can adapt the search behavior during the optimization process.

Disadvantages:
- The performance depends on the choice of the population size (μ) and the number of offspring (λ).
- May require a large number of fitness evaluations to converge.
- Not guaranteed to find the global optimum for non-convex problems.

## Heuristics

### Population Size (μ)

- Choose μ based on the dimensionality and complexity of the problem. A larger μ can help maintain diversity and explore the search space more effectively, but it also increases the computational cost per iteration.
- A common heuristic is to set μ proportional to the square root of the problem dimensionality.

### Number of Offspring (λ)

- Choose λ larger than μ to encourage exploration and maintain diversity in the population. A common ratio is λ = 7μ.
- Increasing λ can improve the chances of finding better solutions, but it also increases the computational cost per iteration.

### Mutation Step Size

- The initial mutation step size should be chosen based on the expected range of the decision variables. A common heuristic is to set the initial step size to about 1/10 of the decision variable range.
- Adapt the mutation step size during the search process based on the success rate of the offspring solutions. Increase the step size if the success rate is high, and decrease it if the success rate is low.
- Consider using self-adaptation mechanisms, where each candidate solution has its own mutation step size that evolves along with the solution.

### Termination Criterion

- Specify a maximum number of iterations or function evaluations based on the available computational budget.
- Monitor the progress of the search and stop if the best fitness value does not improve for a certain number of iterations (stagnation detection).
- Consider using a relative improvement threshold as a termination criterion, stopping the search if the relative improvement in the best fitness value falls below a specified threshold.