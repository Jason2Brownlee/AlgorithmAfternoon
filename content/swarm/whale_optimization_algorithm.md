# Whale Optimization Algorithm

## Name

Whale Optimization Algorithm (WOA)

## Taxonomy

The Whale Optimization Algorithm is a biologically inspired optimization algorithm that falls under the category of swarm intelligence and metaheuristic optimization techniques. It is closely related to other nature-inspired algorithms such as Particle Swarm Optimization (PSO) and the Bat Algorithm.

- Artificial Intelligence
  - Computational Intelligence
    - Biologically Inspired Computation
      - Swarm Intelligence
        - Whale Optimization Algorithm

## Strategy

The Whale Optimization Algorithm is inspired by the bubble-net hunting strategy employed by humpback whales. This hunting behavior involves creating bubble nets to encircle and trap prey, which is modeled in the algorithm as a combination of exploration and exploitation phases.

### Exploration Phase

In the exploration phase, search agents (whales) move around the search space by following a randomly chosen search agent and updating their positions based on the best solution found so far. This allows the algorithm to explore different regions of the search space and maintain diversity in the population.

### Exploitation Phase

The exploitation phase mimics the bubble-net attacking behavior of humpback whales. In this phase, search agents update their positions by moving towards the best solution found so far, simulating the shrinking of the bubble net. This phase allows the algorithm to intensify the search around promising solutions and refine the current best solution.

The Whale Optimization Algorithm balances between exploration and exploitation by adaptively adjusting the search process based on a probability parameter. This parameter determines the likelihood of a search agent to either follow a randomly chosen agent or move towards the best solution.

## Procedure

### Data Structures

- `population`: An array of search agents (whales) representing potential solutions to the optimization problem.
- `fitness`: An array storing the fitness value of each search agent in the population.
- `best_solution`: The best solution found so far during the optimization process.

### Parameters

- `population_size`: The number of search agents (whales) in the population.
- `max_iterations`: The maximum number of iterations allowed for the optimization process.
- `search_space_min`: The minimum value for each dimension of the search space.
- `search_space_max`: The maximum value for each dimension of the search space.
- `a`: A parameter that controls the balance between exploration and exploitation.
- `b`: A parameter that defines the shape of the logarithmic spiral for the bubble-net attacking behavior.

### Procedure

1. Initialize a population of search agents (whales) randomly within the search space.
2. Evaluate the fitness of each search agent in the population.
3. Set the best solution to the search agent with the best fitness value.
4. While the stopping criterion is not met (e.g., maximum iterations):
   1. For each search agent in the population:
      1. Generate a random number `r` between 0 and 1.
      2. If `r` is less than 0.5:
         1. Update the position of the search agent by following a randomly chosen search agent.
      3. Else:
         1. Update the position of the search agent by moving towards the best solution using the bubble-net attacking behavior.
   2. Evaluate the fitness of each updated search agent.
   3. Update the best solution if a better solution is found.
   4. Update the parameter `a` to control the balance between exploration and exploitation.
5. Return the best solution found.

## Considerations

### Advantages

- Simplicity: The Whale Optimization Algorithm is relatively simple to implement and understand compared to some other metaheuristic algorithms.
- Balance between exploration and exploitation: The algorithm effectively balances between exploring the search space and exploiting promising regions, allowing it to find good solutions.
- Adaptability: The algorithm can be easily adapted to solve various optimization problems by modifying the fitness function and search space representation.

### Disadvantages

- Parameter sensitivity: The performance of the algorithm can be sensitive to the choice of parameter values, such as population size and the maximum number of iterations.
- Convergence speed: The algorithm may have slower convergence compared to some other metaheuristic algorithms, especially for high-dimensional or complex optimization problems.
- Local optima: Like many metaheuristic algorithms, the Whale Optimization Algorithm may sometimes get stuck in local optima, particularly if the search space is highly multimodal.

## Heuristics

### Population Size

- The population size should be large enough to ensure diversity and exploration of the search space, but not so large that it significantly increases computational cost.
- A typical range for population size is between 20 and 100, depending on the complexity of the problem.

### Maximum Iterations

- The maximum number of iterations should be set based on the available computational resources and the desired solution quality.
- Increasing the maximum iterations allows the algorithm more time to converge and potentially find better solutions, but also increases the computational cost.
- A common approach is to set the maximum iterations based on the problem size and the observed convergence behavior during initial runs.

### Balancing Exploration and Exploitation

- The parameter `a` controls the balance between exploration and exploitation in the Whale Optimization Algorithm.
- Decreasing the value of `a` over the course of the optimization process can help transition from exploration to exploitation as the algorithm progresses.
- A common strategy is to linearly decrease `a` from 2 to 0 over the iterations, allowing more exploration in the early stages and more exploitation in the later stages.

### Search Space Boundaries

- The search space boundaries (`search_space_min` and `search_space_max`) should be set based on the constraints and feasible regions of the optimization problem.
- Properly defining the search space boundaries can help the algorithm focus on relevant regions and avoid wasting computational resources on infeasible solutions.

### Spiral Shape Parameter

- The parameter `b` defines the shape of the logarithmic spiral used in the bubble-net attacking behavior.
- The default value of `b` is typically set to 1, which creates a spiral that balances between exploitation and exploration.
- Adjusting the value of `b` can influence the spiral shape and the balance between local and global search, but the default value often works well for most problems.
