# Elitist Ant System

## Name

Elitist Ant System, EAS

## Taxonomy

The Elitist Ant System is a variant of the Ant Colony Optimization (ACO) algorithm, which belongs to the field of Swarm Intelligence, a subfield of Computational Intelligence and Biologically Inspired Computation.

- Computational Intelligence
  - Biologically Inspired Computation
    - Swarm Intelligence
      - Ant Colony Optimization (ACO)
        - Ant System (AS)
        - Elitist Ant System (EAS)

## Strategy

The Elitist Ant System is an extension of the Ant System (AS) that introduces an elitist strategy to intensify the search around the best-so-far solution. In EAS, after each iteration, the pheromone trails are updated not only by the ants that have completed their tours but also by an additional amount of pheromone deposited on the edges belonging to the best-so-far tour. This elitist pheromone update reinforces the exploitation of the most promising solutions and helps the algorithm converge faster towards high-quality solutions.

The elitist strategy in EAS is inspired by the concept of elitism in evolutionary algorithms, where the best individuals in a population are preserved or given additional opportunities to influence the search process. By giving extra weight to the best-so-far solution, EAS strikes a balance between exploration and exploitation, allowing the algorithm to focus on the most promising regions of the search space while still maintaining diversity through the regular pheromone updates performed by the ants.

### Pheromone Update

In EAS, the pheromone update consists of two components: the regular pheromone update performed by the ants and the elitist pheromone update based on the best-so-far solution. The regular pheromone update follows the same procedure as in the Ant System, where each ant deposits an amount of pheromone proportional to the quality of its solution on the edges it has traversed. The elitist pheromone update adds an additional amount of pheromone on the edges belonging to the best-so-far tour, effectively reinforcing the most promising solution found so far.

### Pheromone Evaporation

Pheromone evaporation is a crucial component of EAS, as it helps to avoid premature convergence and stagnation. After each iteration, a certain amount of pheromone is evaporated from all edges, allowing the algorithm to forget suboptimal solutions and explore new regions of the search space. The evaporation rate is a parameter that controls the balance between exploration and exploitation, with higher evaporation rates promoting exploration and lower rates favoring exploitation.

## Procedure

### Data Structures
- Pheromone Matrix: A 2D matrix storing the pheromone levels between each pair of nodes in the graph.
- Ant: A structure representing an ant, which contains the following attributes:
  - Current Node: The node where the ant is currently located.
  - Tour: An array storing the nodes visited by the ant in the current iteration.
  - Tour Length: The total length of the ant's tour.
- Best Tour: An array storing the best tour found so far.
- Best Tour Length: The length of the best tour found so far.

### Parameters
- Number of Ants: The number of ants in the colony.
- Number of Iterations: The maximum number of iterations to run the algorithm.
- Alpha: The weight of the pheromone trail in the probabilistic transition rule.
- Beta: The weight of the heuristic information in the probabilistic transition rule.
- Rho: The pheromone evaporation rate.
- Q: A constant used to update the pheromone levels.
- Elitist Weight: The weight given to the best-so-far tour in the pheromone update.

### Steps
1. Initialize the pheromone matrix
   1. Set all elements of the pheromone matrix to a small positive value.
2. For each iteration:
   1. Construct ant solutions
      1. For each ant:
         1. Place the ant on a randomly selected starting node.
         2. While the ant's tour is not complete:
            1. Select the next node to visit based on the probabilistic transition rule, considering the pheromone levels and heuristic information.
            2. Move the ant to the selected node and add it to the ant's tour.
         3. Calculate the length of the ant's tour.
   2. Update the best tour
      1. For each ant:
         1. If the ant's tour length is shorter than the best tour length:
            1. Update the best tour and best tour length with the ant's tour and tour length.
   3. Update pheromone levels
      1. Evaporate pheromone on all edges
         1. For each pair of nodes (i, j):
            1. Reduce the pheromone level on the edge (i, j) by a factor of (1 - rho).
      2. Deposit pheromone on the edges used by the ants
         1. For each ant:
            1. For each edge (i, j) in the ant's tour:
               1. Increase the pheromone level on the edge (i, j) by an amount proportional to the inverse of the ant's tour length.
      3. Deposit additional pheromone on the edges of the best-so-far tour
         1. For each edge (i, j) in the best tour:
            1. Increase the pheromone level on the edge (i, j) by an amount proportional to the inverse of the best tour length multiplied by the elitist weight.
3. Return the best tour and best tour length.

## Considerations

Advantages:
- Faster convergence: The elitist pheromone update helps the algorithm converge faster towards high-quality solutions by intensifying the search around the best-so-far solution.
- Improved solution quality: By giving extra weight to the most promising solutions, EAS often finds better solutions compared to the standard Ant System.
- Balances exploration and exploitation: The elitist strategy allows EAS to focus on the most promising regions of the search space while still maintaining diversity through the regular pheromone updates.

Disadvantages:
- Parameter sensitivity: The performance of EAS can be sensitive to the values of its parameters, particularly the elitist weight (e). Improper parameter settings may lead to premature convergence or insufficient exploitation of the best solutions.
- Potential for stagnation: If the elitist weight is set too high, EAS may converge too quickly to suboptimal solutions and get stuck in local optima.
- Limited exploration: The strong emphasis on the best-so-far solution may reduce the algorithm's ability to explore new regions of the search space, potentially missing better solutions.

## Heuristics

### Parameter Settings
- Number of ants (m): Set the number of ants to a value proportional to the problem size (e.g., number of nodes in the graph). A common heuristic is to use m = n, where n is the number of nodes.
- Alpha (α) and Beta (β): Balance the importance of pheromone and heuristic information. Typical values range from 1 to 5, with α = 1 and β = 2 being common choices. Higher values of α emphasize pheromone, while higher values of β give more weight to heuristic information.
- Rho (ρ): Set the pheromone evaporation rate to a value between 0 and 1. Higher values promote exploration, while lower values favor exploitation. A common range is 0.1 to 0.5.
- Elitist weight (e): Determine the weight given to the best-so-far solution in the elitist pheromone update. A value between 1 and 5 is typically used, with e = 1 being a common choice. Higher values intensify the search around the best-so-far solution, while lower values maintain more diversity.

### Initialization
- Pheromone initialization: Set the initial pheromone levels on all edges to a small positive value to encourage exploration in the early stages of the search. A common heuristic is to set the initial pheromone to τ0 = 1 / (n * Lnn), where n is the number of nodes and Lnn is the length of a nearest-neighbor tour.

### Termination Criteria
- Maximum iterations: Set a maximum number of iterations as a stopping criterion to prevent the algorithm from running indefinitely. The specific value depends on the problem size and desired solution quality.
- Stagnation detection: Implement a stagnation detection mechanism to terminate the algorithm if no improvement in the best-so-far solution is observed for a certain number of iterations. This helps to avoid wasting computational resources when the algorithm is unlikely to find better solutions.

### Local Search
- Incorporate local search techniques: Consider integrating local search methods, such as 2-opt or 3-opt, to refine the solutions constructed by the ants. Local search can help improve the quality of solutions and speed up convergence.

