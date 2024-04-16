# Iterated Local Search

## Name
Iterated Local Search (ILS)

## Taxonomy
Iterated Local Search is a metaheuristic optimization algorithm that combines local search with perturbation steps to escape local optima. It is closely related to other metaheuristics such as Variable Neighborhood Search (VNS) and Greedy Randomized Adaptive Search Procedure (GRASP).

- Optimization
  - Metaheuristics
    - Stochastic Optimization
      - Iterated Local Search (ILS)

## Strategy
Iterated Local Search is a simple yet powerful optimization strategy that alternates between intensification and diversification phases. The intensification phase involves applying a local search procedure to improve the current solution until a local optimum is reached. Once the local search cannot provide further improvements, the diversification phase is triggered, where a perturbation operator is applied to the current solution to escape the local optimum and explore new regions of the search space.

The perturbation step is crucial in ILS, as it must strike a balance between introducing enough change to the current solution to escape the local optimum, while still retaining some of the good characteristics of the solution. After the perturbation, the local search procedure is applied again to the modified solution, and the process repeats until a termination criterion is met, such as a maximum number of iterations or a time limit.

ILS maintains the best solution found throughout the search process and returns it as the final output. The algorithm's effectiveness depends on the choice of the local search procedure and the perturbation operator, which can be tailored to the specific problem at hand.

## Procedure
Data Structures:
- `current_solution`: The current solution being explored.
- `best_solution`: The best solution found so far.

Parameters:
- `max_iterations`: The maximum number of iterations allowed.
- `perturbation_strength`: The strength of the perturbation applied to the current solution.

Steps:
1. Initialize:
   1. Generate an initial solution and assign it to `current_solution`.
   2. Apply the local search procedure to `current_solution` until a local optimum is reached.
   3. Set `best_solution` to `current_solution`.
   4. Set `iteration_count` to 0.

2. While `iteration_count` is less than `max_iterations`:
   1. Apply the perturbation operator to `current_solution` based on `perturbation_strength`.
   2. Apply the local search procedure to the perturbed solution until a local optimum is reached.
   3. If the new local optimum is better than `best_solution`, update `best_solution`.
   4. If an acceptance criterion is met (e.g., always accept or accept with a certain probability), set `current_solution` to the new local optimum.
   5. Increment `iteration_count` by 1.

3. Return `best_solution` as the final output.

## Considerations
Advantages:
- Simplicity: ILS is easy to implement and requires only a few components, namely a local search procedure and a perturbation operator.
- Flexibility: ILS can be adapted to various optimization problems by choosing appropriate local search and perturbation strategies.
- Efficiency: By combining intensification and diversification, ILS can efficiently explore the search space and find high-quality solutions.

Disadvantages:
- Parameter sensitivity: The performance of ILS can be sensitive to the choice of parameters, such as the perturbation strength and acceptance criterion.
- Local search dependency: The effectiveness of ILS heavily depends on the quality of the underlying local search procedure.
- Lack of problem-specific knowledge: ILS does not inherently incorporate problem-specific knowledge, which may limit its performance on certain problems compared to specialized algorithms.

## Heuristics
Perturbation Strength:
- Start with a small perturbation strength and gradually increase it if the search gets stuck in local optima.
- Adjust the perturbation strength based on the problem size and complexity.
- Experiment with different perturbation operators, such as random moves, swaps, or restarts.

Local Search Procedure:
- Choose a local search procedure that is well-suited for the problem at hand, such as hill climbing, simulated annealing, or tabu search.
- Consider the trade-off between the quality of the local search and its computational cost.
- Implement efficient data structures and incremental evaluation techniques to speed up the local search.

Acceptance Criterion:
- Always accepting the new local optimum can lead to a more explorative search but may also result in slower convergence.
- Accepting the new local optimum only if it improves the current solution can lead to a more exploitative search but may get stuck in local optima.
- Consider probabilistic acceptance criteria, such as the Metropolis criterion used in simulated annealing, to balance exploration and exploitation.

Termination Criteria:
- Set a maximum number of iterations or a time limit to control the overall runtime of the algorithm.
- Implement early stopping mechanisms based on the progress of the search, such as stopping if no improvement is observed for a certain number of iterations.
- Consider problem-specific termination criteria, such as reaching a target solution quality or satisfying certain constraints.

Hybridization:
- Combine ILS with other metaheuristics or problem-specific heuristics to improve its performance.
- Incorporate domain knowledge or problem-specific operators into the perturbation step or local search procedure.
- Use ILS as a component within a larger optimization framework, such as a memetic algorithm or a hybrid evolutionary algorithm.

