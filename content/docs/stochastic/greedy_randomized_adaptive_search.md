# Greedy Randomized Adaptive Search

## Name
Greedy Randomized Adaptive Search (GRASP)

## Taxonomy
GRASP is a metaheuristic optimization algorithm that combines the principles of greedy algorithms and local search techniques. It is closely related to other metaheuristics such as Simulated Annealing and Tabu Search.

- Optimization
  - Metaheuristics
    - Stochastic Optimization
      - Greedy Randomized Adaptive Search (GRASP)

## Strategy
GRASP is an iterative process that consists of two main phases: the construction phase and the local search phase. In the construction phase, a feasible solution is built by iteratively adding elements to a partial solution. The selection of the next element to be added is determined by a greedy function that measures the contribution of each candidate element to the objective function. However, instead of always choosing the best candidate, a restricted candidate list (RCL) is maintained, which contains a subset of the most promising candidates. The element to be added is randomly selected from the RCL, introducing a degree of randomness into the construction process.

Once a complete solution is obtained, the local search phase is applied to improve it. The local search explores the neighborhood of the current solution by making small modifications and accepting the changes if they lead to a better objective function value. This process continues until no further improvements can be made or a predefined termination criterion is met.

The combination of the greedy construction phase and the local search phase allows GRASP to strike a balance between the intensification of the search in promising regions of the solution space and the diversification of the search to explore new areas.

## Procedure
1. Initialize:
   - Define the problem-specific data structures and parameters.
   - Set the termination criterion (e.g., maximum number of iterations or time limit).
2. Repeat until the termination criterion is met:
   - Construction Phase:
     1. Initialize an empty solution.
     2. While the solution is not complete:
        - Evaluate the candidate elements using a greedy function.
        - Build the restricted candidate list (RCL) with the most promising candidates.
        - Randomly select an element from the RCL and add it to the partial solution.
     3. Return the complete solution.
   - Local Search Phase:
     1. Define the neighborhood structure for the current solution.
     2. While the termination criterion for the local search is not met:
        - Generate a neighboring solution by making a small modification to the current solution.
        - Evaluate the objective function value of the neighboring solution.
        - If the neighboring solution is better, accept it as the new current solution.
     3. Return the best solution found during the local search.
   - Update the best solution found so far if necessary.
3. Return the best solution found.

### Data Structures
- Solution: Represents a complete or partial solution to the problem. Its structure depends on the specific problem being solved (e.g., a permutation for a scheduling problem or a binary vector for a subset selection problem).
- Candidate List: A list or array containing the candidate elements that can be added to the partial solution during the construction phase.
- Restricted Candidate List (RCL): A subset of the candidate list containing the most promising candidates according to the greedy function.

### Parameters
- Alpha: A parameter that controls the balance between greediness and randomness in the construction phase. It determines the size of the RCL. A value of 0 corresponds to a purely greedy construction, while a value of 1 results in a completely random construction.
- Max Iterations: The maximum number of iterations the algorithm will run before terminating.
- Local Search Iterations: The maximum number of iterations for the local search phase within each main iteration.

## Considerations
### Advantages
- GRASP is a simple and flexible metaheuristic that can be easily adapted to various optimization problems.
- It provides a good balance between the intensification and diversification of the search, allowing it to explore promising regions while avoiding getting stuck in local optima.
- GRASP can often find high-quality solutions in a reasonable amount of time, making it suitable for practical applications.

### Disadvantages
- The performance of GRASP heavily depends on the design of the greedy function and the neighborhood structure used in the local search phase. Developing effective problem-specific components requires domain knowledge and experimentation.
- GRASP does not provide any guarantee on the optimality of the solutions found. It is a heuristic approach that aims to find good solutions but may not necessarily reach the global optimum.
- The randomness introduced in the construction phase can lead to variability in the quality of the solutions obtained across different runs of the algorithm.

## Heuristics
### Greedy Function Design
- The greedy function should measure the contribution of each candidate element to the objective function, considering both the immediate impact and the potential future impact on the solution quality.
- The greedy function should be computationally efficient to evaluate, as it is called multiple times during the construction phase.
- If possible, incorporate problem-specific knowledge and heuristics into the greedy function to guide the construction process towards promising solutions.

### Restricted Candidate List (RCL) Size
- The size of the RCL determines the balance between greediness and randomness in the construction phase. A smaller RCL leads to a more greedy construction, while a larger RCL introduces more randomness.
- Experiment with different values of the alpha parameter to find a suitable trade-off between solution quality and diversification.
- Consider adapting the RCL size dynamically during the search process, starting with a larger RCL to encourage exploration and gradually reducing its size to intensify the search in promising regions.

### Local Search Neighborhood Structure
- Define a neighborhood structure that allows for effective exploration of the solution space around the current solution.
- The neighborhood structure should be problem-specific and consider the characteristics of the solution representation and the problem constraints.
- Strike a balance between the size of the neighborhood and the computational cost of exploring it. A larger neighborhood may lead to better solutions but can be more time-consuming to search.

### Termination Criteria
- Set a reasonable maximum number of iterations or a time limit based on the problem size and the available computational resources.
- Consider implementing additional termination criteria, such as stopping the search if no improvement has been found for a certain number of iterations or if the solution quality reaches a predefined threshold.
- Monitor the progress of the search and adjust the termination criteria dynamically if necessary. For example, if the search appears to be stagnating, consider increasing the number of iterations or exploring alternative neighborhood structures.

### Hybridization
- GRASP can be combined with other optimization techniques to enhance its performance or to address specific problem characteristics.
- Consider incorporating problem-specific heuristics or local search techniques into the construction phase or the local search phase to improve the quality of the solutions.
- Explore the possibility of using GRASP as a component within a larger optimization framework, such as a multi-start approach or a population-based metaheuristic like Genetic Algorithms or Ant Colony Optimization.

