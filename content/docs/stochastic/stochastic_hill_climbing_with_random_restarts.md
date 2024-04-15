# Stochastic Hill Climbing With Random-Restarts

## Name

Stochastic Hill Climbing With Random-Restarts (SHCR)

## Taxonomy

Stochastic Hill Climbing With Random-Restarts is a local search metaheuristic that belongs to the broader field of Stochastic Optimization. It is closely related to other hill climbing algorithms such as Simple Hill Climbing and Stochastic Hill Climbing.

- Artificial Intelligence
  - Computational Intelligence
    - Stochastic Optimization
      - Metaheuristics
        - Local Search Algorithms
          - Hill Climbing Algorithms
            - Stochastic Hill Climbing With Random-Restarts

## Strategy

Stochastic Hill Climbing With Random-Restarts is a local search algorithm that aims to find the global optimum in a search space by iteratively improving a candidate solution. The algorithm starts with a random initial solution and attempts to find better solutions by randomly perturbing the current solution and accepting the new solution if it improves the objective function value.

### Stochastic Search

Unlike Simple Hill Climbing, which deterministically selects the best neighboring solution at each iteration, Stochastic Hill Climbing introduces randomness in the search process. This randomness allows the algorithm to escape local optima by occasionally accepting worse solutions, increasing the chances of finding the global optimum.

### Random Restarts

To further improve the algorithm's ability to find the global optimum, Stochastic Hill Climbing With Random-Restarts incorporates multiple restarts from different initial solutions. When the algorithm reaches a local optimum or a maximum number of iterations, it restarts the search from a new randomly generated solution. This process is repeated for a fixed number of restarts or until a satisfactory solution is found.

## Procedure

### Data Structures

1. `current_solution`: The current candidate solution.
2. `best_solution`: The best solution found so far.
3. `objective_function`: A function that evaluates the quality of a solution.

### Parameters

1. `max_iterations`: The maximum number of iterations allowed for each hill climbing run.
2. `num_restarts`: The number of random restarts to perform.
3. `step_size`: The magnitude of the perturbation applied to the current solution.

### Algorithm Steps

1. Initialize `best_solution` to None.
2. For `num_restarts` times:
   1. Generate a random initial solution and assign it to `current_solution`.
   2. For `max_iterations` times:
      1. Perturb `current_solution` by applying a random modification of magnitude `step_size` to obtain a new solution.
      2. Evaluate the objective function for the new solution.
      3. If the new solution is better than `current_solution`, update `current_solution` to the new solution.
      4. If `current_solution` is better than `best_solution`, update `best_solution` to `current_solution`.
   3. If a satisfactory solution is found, terminate the algorithm.
3. Return `best_solution`.

## Considerations

### Advantages

- Simple and easy to implement.
- Can escape local optima due to the randomness introduced in the search process.
- Multiple restarts increase the chances of finding the global optimum.

### Disadvantages

- The algorithm's performance heavily depends on the choice of parameters, such as `step_size` and `max_iterations`.
- May require a large number of objective function evaluations, which can be computationally expensive for complex problems.
- The random nature of the search may lead to inconsistent results across different runs.

## Heuristics

### Parameter Selection

- Choose `max_iterations` based on the available computational resources and the complexity of the problem. A higher value increases the chances of finding better solutions but also increases the computational cost.
- Set `num_restarts` to a value that balances the tradeoff between exploration and exploitation. More restarts increase the likelihood of finding the global optimum but also increase the overall runtime.
- Adjust `step_size` based on the characteristics of the search space. A larger `step_size` allows for broader exploration but may skip over good solutions, while a smaller `step_size` enables fine-tuning but may lead to slower convergence.

### Problem-Specific Considerations

- Define an appropriate objective function that accurately captures the quality of a solution for the given problem.
- Consider the structure of the search space and design suitable perturbation mechanisms that effectively explore the solution space.
- Incorporate domain knowledge, when available, to guide the search process and improve the quality of the generated solutions.

### Termination Criteria

- In addition to the maximum number of iterations, consider implementing alternative termination criteria, such as:
  - Reaching a predefined target objective function value.
  - Detecting convergence, i.e., when the improvement in the objective function value falls below a certain threshold.
  - Imposing a time limit on the algorithm's execution.

### Hybridization

- Consider combining Stochastic Hill Climbing With Random-Restarts with other optimization techniques, such as local search algorithms or evolutionary algorithms, to further improve its performance.
- Incorporate problem-specific heuristics or domain knowledge to guide the search process and generate higher-quality solutions.
