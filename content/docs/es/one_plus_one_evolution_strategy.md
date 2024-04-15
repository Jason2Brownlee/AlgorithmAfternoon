---
title: (1+1)-Evolution Strategy
---
# (1+1)-Evolution Strategy

## Name

(1+1)-Evolution Strategy, (1+1)-ES, (1+1) Evolution Strategy, (1+1) ES

## Taxonomy

The (1+1)-Evolution Strategy is a simple, single-solution based Evolutionary Algorithm that belongs to the field of Evolutionary Computation, a subfield of Computational Intelligence.

- Computational Intelligence
  - Evolutionary Computation
    - Evolutionary Algorithms
      - Evolution Strategies
        - (1+1)-Evolution Strategy

## Strategy

The (1+1)-Evolution Strategy is a simple, single-solution based optimization algorithm inspired by the principles of biological evolution. It maintains a single candidate solution, often referred to as the parent, and iteratively attempts to improve it through a process of mutation and selection.

### Mutation

In each iteration, the algorithm creates a new candidate solution, called the offspring, by applying a mutation operator to the parent. The mutation operator typically involves adding a random perturbation to the parent's decision variables, often drawn from a normal distribution with zero mean and a specified standard deviation.

### Selection

After the offspring is generated, the algorithm compares its fitness (objective function value) with that of the parent. If the offspring has a better fitness, it replaces the parent and becomes the new parent for the next iteration. If the parent has a better fitness, it is retained, and the offspring is discarded.

This simple selection mechanism ensures that the algorithm always moves towards better solutions and never accepts a worse solution. The process of mutation and selection continues for a specified number of iterations or until a termination criterion is met.

## Procedure

### Data Structures

- `parent`: The current candidate solution
- `offspring`: The new candidate solution generated through mutation
- `fitness(solution)`: A function that evaluates the fitness (objective function value) of a given solution

### Parameters

- `mu`: The mean of the normal distribution used for mutation (typically set to 0)
- `sigma`: The standard deviation of the normal distribution used for mutation
- `max_iterations`: The maximum number of iterations to run the algorithm

### Pseudocode

1. Initialize `parent` with a random candidate solution
2. For `i` = 1 to `max_iterations`:
   1. Generate `offspring` by mutating `parent`:
      1. For each decision variable `x` in `parent`:
         1. `offspring[x] = parent[x] + Normal(mu, sigma)`
   2. If `fitness(offspring)` is better than `fitness(parent)`:
      1. `parent = offspring`
3. Return `parent` as the best found solution

## Considerations

### Advantages

- Simplicity: The (1+1)-Evolution Strategy is easy to understand and implement due to its minimal structure and simple mutation and selection operators.
- Few parameters: The algorithm has only a few parameters to tune, namely the mutation strength (standard deviation) and the termination criterion, making it less sensitive to parameter settings compared to more complex algorithms.
- Local search: The (1+1)-ES can effectively explore the local neighborhood of a candidate solution, making it suitable for fine-tuning and local optimization.

### Disadvantages

- Limited exploration: Due to its single-solution nature and simple mutation operator, the (1+1)-ES may struggle to escape local optima and explore different regions of the search space effectively.
- Slow convergence: The algorithm may require a large number of iterations to converge to a good solution, especially for high-dimensional and complex optimization problems.
- Lack of diversity: The (1+1)-ES does not maintain a population of diverse solutions, which can limit its ability to adapt to multimodal fitness landscapes and find global optima.

## Heuristics

### Mutation Strength (Sigma)

- Start with a relatively large `sigma` value to encourage exploration in the early stages of the search. Gradually decrease `sigma` over the course of the optimization to focus on exploitation and fine-tuning.
- Adapt `sigma` based on the progress of the search. If the algorithm is consistently finding better solutions, increase `sigma` to maintain exploration. If the algorithm is struggling to find improvements, decrease `sigma` to focus on local search.

### Termination Criterion

- Use a combination of maximum iterations and a convergence criterion based on the rate of improvement in fitness. Stop the algorithm if no significant improvement is observed over a specified number of iterations.
- Consider the computational budget and the desired solution quality when setting the termination criterion. Allow more iterations for complex problems or when high-quality solutions are required.

### Initialization

- Initialize the `parent` solution randomly within the feasible search space to provide a diverse starting point for the search.
- If prior knowledge about the problem is available, consider initializing the `parent` solution using a heuristic or a previously known good solution to start the search in a promising region.

### Problem-Specific Modifications

- Adapt the mutation operator to the characteristics of the problem. For example, use different mutation strengths for different decision variables based on their sensitivity or importance.
- Incorporate problem-specific constraints or repair mechanisms to ensure the feasibility of the offspring solutions.

### Hybrid Approaches

- Consider combining the (1+1)-ES with other local search techniques, such as hill climbing or pattern search, to improve its local optimization capabilities.
- Use the (1+1)-ES as a local search operator within a larger population-based Evolutionary Algorithm to balance exploration and exploitation.

