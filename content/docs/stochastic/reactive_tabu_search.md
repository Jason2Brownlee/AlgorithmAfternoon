# Reactive Tabu Search

## Name

Reactive Tabu Search, RTS

## Taxonomy

Reactive Tabu Search is a metaheuristic optimization algorithm that extends the Tabu Search method by incorporating reactive mechanisms to adapt the search parameters during the optimization process. It is closely related to other Tabu Search variants, such as Adaptive Tabu Search and Robust Tabu Search.

- Computational Intelligence
  - Stochastic Optimization
    - Metaheuristics
      - Trajectory Methods
        - Tabu Search
          - Reactive Tabu Search

## Strategy

### Tabu Search Foundation

Reactive Tabu Search builds upon the core principles of Tabu Search, which is a local search-based optimization algorithm. The algorithm explores the solution space by iteratively moving from the current solution to a neighboring solution, even if the move leads to a worse objective function value. To prevent the search from revisiting recently explored solutions and getting trapped in local optima, Tabu Search maintains a tabu list that stores the moves or solution attributes that are forbidden for a certain number of iterations.

### Reactive Mechanisms

The key distinguishing feature of Reactive Tabu Search is the incorporation of reactive mechanisms that dynamically adjust the search parameters based on the search history and the characteristics of the problem landscape. These mechanisms aim to improve the algorithm's ability to adapt to different problem instances and to balance the exploration and exploitation aspects of the search process.

The reactive mechanisms in Reactive Tabu Search typically involve adjusting the size of the tabu list and the aspiration criteria. The tabu list size determines the number of iterations for which a move or solution attribute remains tabu, while the aspiration criteria allow the algorithm to override the tabu status of a move if it leads to a solution with a better objective function value than the current best-known solution.

### Feedback-Based Parameter Adaptation

Reactive Tabu Search employs a feedback mechanism to adapt the search parameters based on the search progress. The algorithm monitors the search history and collects information about the quality of the visited solutions, the frequency of solution cycling, and the level of diversification achieved.

Based on this feedback, the algorithm dynamically adjusts the tabu list size and the aspiration criteria. If the search is stuck in a local optimum or cycles between previously visited solutions, the tabu list size is increased to promote diversification and encourage the exploration of new regions of the solution space. Conversely, if the search consistently finds improving solutions, the tabu list size is decreased to intensify the search in promising areas.

## Procedure

### Data Structures

- `current_solution`: The current solution being explored.
- `best_solution`: The best solution found so far.
- `tabu_list`: A list of tabu moves or solution attributes.
- `search_history`: A record of the visited solutions and their objective function values.

### Parameters

- `max_iterations`: The maximum number of iterations allowed.
- `initial_tabu_tenure`: The initial length of the tabu list.
- `min_tabu_tenure`: The minimum allowed length of the tabu list.
- `max_tabu_tenure`: The maximum allowed length of the tabu list.
- `aspiration_threshold`: The threshold for overriding the tabu status of a move.

### Reactive Tabu Search Algorithm

1. Initialize:
   - Generate an initial solution and set it as the `current_solution` and `best_solution`.
   - Initialize the `tabu_list` to be empty.
   - Set the `tabu_tenure` to `initial_tabu_tenure`.

2. While the stopping criteria are not met (e.g., `max_iterations` is not reached):
   1. Generate a set of candidate neighboring solutions.
   2. Evaluate the objective function value for each candidate solution.
   3. Select the best candidate solution that is either not in the `tabu_list` or satisfies the aspiration criteria.
   4. Update the `current_solution` with the selected candidate solution.
   5. If the `current_solution` is better than the `best_solution`, update the `best_solution`.
   6. Add the selected move or solution attributes to the `tabu_list`.
   7. If the `tabu_list` size exceeds the `tabu_tenure`, remove the oldest entry.
   8. Update the `search_history` with the `current_solution` and its objective function value.
   9. Adapt the `tabu_tenure` based on the search history:
      - If the search is stuck in a local optimum or cycles are detected, increase the `tabu_tenure` (up to `max_tabu_tenure`).
      - If the search consistently finds improving solutions, decrease the `tabu_tenure` (down to `min_tabu_tenure`).

3. Return the `best_solution` found.

## Considerations

### Advantages

- Reactive Tabu Search can adapt to different problem instances and landscapes by dynamically adjusting the search parameters based on the search history.
- The reactive mechanisms help balance the exploration and exploitation aspects of the search process, enabling the algorithm to escape local optima and explore promising regions more effectively.
- Reactive Tabu Search can often find high-quality solutions faster than traditional Tabu Search by adapting the search parameters to the problem characteristics.

### Disadvantages

- The effectiveness of Reactive Tabu Search depends on the proper design and tuning of the reactive mechanisms, which may require problem-specific knowledge and experimentation.
- The additional computations involved in monitoring the search history and adapting the search parameters can increase the overall computational complexity of the algorithm compared to traditional Tabu Search.
- The performance of Reactive Tabu Search may be sensitive to the initial solution and the choice of the initial search parameters, such as the initial tabu list size.

## Heuristics

### Tabu List Management

- Start with a relatively small initial tabu list size and allow the reactive mechanisms to adapt it during the search process.
- Ensure that the tabu list size does not become too large, as it may overly restrict the search and hinder the exploration of promising solutions.
- Consider using a dynamic tabu list size that adapts based on the search progress and the characteristics of the problem landscape.

### Aspiration Criteria

- Use aspiration criteria that allow the algorithm to override the tabu status of a move if it leads to a solution with a better objective function value than the current best-known solution.
- Adjust the aspiration threshold based on the search progress and the quality of the visited solutions. A higher threshold may be appropriate when the search consistently finds improving solutions, while a lower threshold may be beneficial when the search is stuck in a local optimum.

### Reactive Parameter Adaptation

- Monitor the search history and collect relevant information, such as the quality of the visited solutions, the frequency of solution cycling, and the level of diversification achieved.
- Define appropriate thresholds and rules for triggering the adaptation of the tabu list size and aspiration criteria based on the search feedback.
- Strike a balance between reacting to the search progress and allowing sufficient time for the current parameter settings to take effect. Avoid overly frequent or drastic parameter changes that may disrupt the search process.

### Neighborhood Selection

- Choose a neighborhood structure that allows for meaningful and diverse moves while maintaining the feasibility of the solutions.
- Consider using multiple neighborhood structures or adaptive neighborhood selection mechanisms to enhance the exploration capabilities of the algorithm.

### Stopping Criteria

- Specify a maximum number of iterations or a time limit to terminate the search process.
- Implement additional stopping criteria based on the search progress, such as the number of consecutive non-improving iterations or the relative improvement in the objective function value.
- Allow for early termination if the search reaches a satisfactory solution quality or if the algorithm converges to a stable state.

