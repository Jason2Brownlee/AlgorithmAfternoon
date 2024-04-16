# Rank-Based Ant System

## Name

Rank-Based Ant System (RBAS), Rank-Based AS, ASrank, RAS

## Taxonomy

Rank-Based Ant System is a variant of Ant System, which is an algorithmic technique in the field of Ant Colony Optimization (ACO), a subfield of Swarm Intelligence, Metaheuristics, and Computational Intelligence. It is closely related to other ACO algorithms such as Ant System, Ant Colony System, and MAX-MIN Ant System.

- Computational Intelligence
  - Swarm Intelligence
    - Ant Colony Optimization (ACO)
      - Ant System (AS)
        - Rank-Based Ant System (RBAS)

## Strategy

The Rank-Based Ant System introduces a rank-based pheromone update mechanism to the original Ant System algorithm. In RBAS, only the best-ranked ants are allowed to deposit pheromones, as opposed to all ants in the original AS.

### Rank-Based Pheromone Update

After each iteration, the ants are sorted according to their solution quality. Only the top-ranked ants (typically a fixed number) are selected to deposit pheromones on the edges they have traversed. The amount of pheromone deposited by each ant is proportional to its rank, with higher-ranked ants depositing more pheromone than lower-ranked ants.

This rank-based pheromone update strategy helps to focus the search around the most promising solutions found by the best-performing ants, leading to faster convergence and improved solution quality compared to the original AS.

## Procedure

### Data Structures

- Pheromone Matrix: A 2D matrix representing the pheromone levels on the edges between nodes in the problem graph.
- Ant: A simple agent that constructs solutions by traversing the problem graph, guided by pheromone levels and heuristic information.

### Parameters

- `num_ants`: The number of ants in the colony.
- `num_iterations`: The maximum number of iterations for the algorithm to run.
- `alpha`: The pheromone influence factor, determining the importance of pheromone levels in the ant's decision-making process.
- `beta`: The heuristic influence factor, determining the importance of heuristic information in the ant's decision-making process.
- `evaporation_rate`: The rate at which pheromones evaporate from the edges after each iteration.
- `num_ranked_ants`: The number of top-ranked ants that are allowed to deposit pheromones.

### Algorithm

1. Initialize the pheromone matrix with a small, positive value on all edges.
2. For each iteration:
   1. For each ant:
      1. Construct a solution by traversing the problem graph, guided by pheromone levels and heuristic information.
      2. Evaluate the quality of the constructed solution.
   2. Sort the ants according to their solution quality.
   3. Update the pheromone matrix:
      1. Evaporate pheromones on all edges by multiplying the pheromone levels by (1 - `evaporation_rate`).
      2. For each of the top `num_ranked_ants` ants:
         1. Deposit pheromones on the edges traversed by the ant, proportional to the ant's rank and solution quality.
3. Return the best solution found across all iterations.

## Considerations

### Advantages

- Faster convergence compared to the original Ant System, due to the focused pheromone update by the best-ranked ants.
- Improved solution quality, as the search is guided more strongly by the most promising solutions found.
- Maintains a balance between exploration and exploitation, preventing premature convergence to suboptimal solutions.

### Disadvantages

- Increased computational complexity due to the need to sort ants by their solution quality after each iteration.
- The performance of the algorithm can be sensitive to the choice of the `num_ranked_ants` parameter, requiring careful tuning for different problem instances.
- Like other ACO algorithms, RBAS may struggle with highly constrained optimization problems or those with many local optima.

## Heuristics

### Parameter Selection

- `num_ants`: A common heuristic is to set the number of ants equal to the number of nodes in the problem graph, ensuring thorough exploration of the search space.
- `alpha` and `beta`: These parameters control the balance between pheromone and heuristic information. Typically, `alpha` is set to a value between 1 and 2, while `beta` is set to a value between 2 and 5, giving more importance to heuristic information.
- `evaporation_rate`: A value between 0.1 and 0.5 is commonly used, allowing for a gradual decay of pheromone levels while maintaining the influence of previous good solutions.
- `num_ranked_ants`: A typical value is around 20-30% of the total number of ants, ensuring that only the most promising solutions influence the pheromone update.

### Problem-Specific Heuristics

- When applying RBAS to a specific problem, it is essential to design an appropriate heuristic function that provides effective guidance for the ants in constructing solutions.
- The heuristic function should be computationally inexpensive and provide a good estimate of the local quality of a decision, such as the distance between nodes in a traveling salesman problem or the resource requirements in a scheduling problem.

### Termination Criteria

- In addition to the maximum number of iterations, consider implementing additional termination criteria based on the progress of the algorithm, such as stopping when the best solution found has not improved for a certain number of iterations.
- Monitoring the convergence of the pheromone levels can also provide insights into the algorithm's progress and help determine an appropriate stopping point.

