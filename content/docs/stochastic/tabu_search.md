# Tabu Search

## Name

Tabu Search, TS

## Taxonomy

Tabu Search is a metaheuristic optimization algorithm that belongs to the field of local search techniques. It is closely related to other local search algorithms such as Hill Climbing and Simulated Annealing.

- Artificial Intelligence
  - Optimization
    - Metaheuristics
      - Local Search
        - Tabu Search

## Strategy

Tabu Search is a local search algorithm that aims to escape local optima by maintaining a tabu list, which is a short-term memory of recently visited solutions or moves. The algorithm explores the solution space by moving from the current solution to its best neighboring solution, even if it leads to a worse objective function value. To prevent cycling back to previously visited solutions, the tabu list forbids certain moves or solutions for a specified number of iterations, known as the tabu tenure.

The algorithm starts with an initial solution and iteratively improves it by applying local search moves. At each iteration, the algorithm generates a set of candidate solutions in the neighborhood of the current solution. The best candidate solution is selected as the new current solution, even if it is worse than the previous one. If the selected move is in the tabu list, it is only accepted if it satisfies an aspiration criterion, which allows the algorithm to override the tabu status of a move if it leads to a solution better than the best solution found so far.

Tabu Search also incorporates intensification and diversification strategies to balance the exploration and exploitation of the solution space. Intensification focuses on exploring promising regions of the solution space more thoroughly, while diversification encourages the algorithm to explore new regions and escape from local optima.

## Procedure

1. Initialize:
   - Generate an initial solution s
   - Set the best solution s_best = s
   - Initialize the tabu list to be empty
   - Set the tabu tenure t
   - Set the maximum number of iterations max_iter
   - Set the current iteration counter iter = 0

2. While iter < max_iter:
   - Generate a set of candidate solutions N(s) in the neighborhood of s
   - Select the best candidate solution s' from N(s) that is not in the tabu list or satisfies the aspiration criterion
   - Update the best solution: if f(s') < f(s_best), set s_best = s'
   - Update the current solution: s = s'
   - Update the tabu list:
     - Add the move that generated s' to the tabu list
     - If the tabu list size exceeds the tabu tenure t, remove the oldest move from the list
   - Increment the iteration counter: iter = iter + 1

3. Return the best solution found s_best

### Data Structures

- Solution: Represents a candidate solution in the solution space
- Tabu List: A list that stores the recently visited solutions or moves
- Aspiration Criterion: A condition that allows the algorithm to override the tabu status of a move

### Parameters

- Tabu Tenure: The number of iterations for which a move or solution remains in the tabu list
- Maximum Iterations: The maximum number of iterations the algorithm will run before terminating
- Neighborhood Size: The number of candidate solutions generated in each iteration

## Considerations

### Advantages

- Tabu Search can escape local optima by allowing moves to worse solutions and preventing cycling back to previously visited solutions
- The tabu list provides a short-term memory mechanism that helps the algorithm explore new regions of the solution space
- Tabu Search is flexible and can be easily adapted to various optimization problems

### Disadvantages

- The performance of Tabu Search depends on the appropriate setting of the tabu tenure and other parameters
- The algorithm may require a large number of iterations to converge to a high-quality solution
- Tabu Search may struggle with highly constrained problems or problems with a large number of local optima

## Heuristics

### Tabu Tenure

- The tabu tenure should be set based on the size and complexity of the problem
- A smaller tabu tenure allows for more exploration but may lead to cycling, while a larger tabu tenure encourages diversification but may slow down the search
- A common heuristic is to set the tabu tenure to a value between 7 and 20, depending on the problem size

### Aspiration Criterion

- The most common aspiration criterion is to allow a tabu move if it leads to a solution better than the best solution found so far
- Other aspiration criteria, such as allowing a tabu move if it has not been visited for a certain number of iterations, can also be used

### Intensification and Diversification

- Intensification strategies can be applied by focusing the search on promising regions of the solution space, such as by re-starting the search from the best solution found so far or by modifying the neighborhood structure to explore solutions similar to the current best solution
- Diversification strategies can be applied by introducing random perturbations to the current solution, by using a larger neighborhood size, or by periodically resetting the search to a new initial solution

### Stopping Criteria

- The algorithm can be terminated after a fixed number of iterations, a specified amount of computational time, or when no improvement has been made for a certain number of iterations
- A common practice is to set a maximum number of iterations based on the problem size and complexity, and to terminate the algorithm if no improvement has been made for a specified number of consecutive iterations

### Neighborhood Structure

- The choice of neighborhood structure depends on the problem being solved and can have a significant impact on the performance of the algorithm
- Common neighborhood structures include swap moves (exchanging two elements), insertion moves (removing an element and inserting it in a different position), and more complex moves that are specific to the problem domain
- The neighborhood size should be large enough to allow for sufficient exploration but not so large that it slows down the search excessively

