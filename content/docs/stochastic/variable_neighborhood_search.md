# Variable Neighborhood Search

## Name

Variable Neighborhood Search (VNS)

## Taxonomy

Variable Neighborhood Search is a metaheuristic optimization algorithm that systematically changes the neighborhood structure during the search process to escape local optima and explore diverse regions of the solution space. It is closely related to other local search-based metaheuristics such as Simulated Annealing and Tabu Search.

- Optimization
  - Metaheuristics
    - Local Search-based Metaheuristics
      - Variable Neighborhood Search

## Strategy

The main idea behind Variable Neighborhood Search is to systematically change the neighborhood structure during the search process. This allows the algorithm to escape local optima and explore different regions of the solution space. The search process alternates between two main phases: the shaking phase and the local search phase.

### Shaking Phase

In the shaking phase, the algorithm generates a new solution by randomly perturbing the current solution. The perturbation is performed using a set of predefined neighborhood structures, which are typically ordered in increasing size or complexity. The shaking phase helps the algorithm to escape local optima and explore new regions of the solution space.

### Local Search Phase

After the shaking phase, the algorithm performs a local search starting from the perturbed solution. The local search aims to find a better solution in the current neighborhood. If an improved solution is found, the search continues from this new solution; otherwise, the algorithm moves to the next neighborhood structure in the predefined set.

The search process iterates between the shaking and local search phases until a stopping criterion is met, such as a maximum number of iterations or a time limit.

## Procedure

1. Initialize the algorithm:
   1. Define the set of neighborhood structures N_k, k = 1, ..., k_max, ordered by increasing size or complexity.
   2. Select an initial solution x.
   3. Set the current best solution x_best = x.
2. Repeat until a stopping criterion is met:
   1. Set k = 1.
   2. Repeat until k = k_max:
      1. Shaking phase: Generate a new solution x' by randomly perturbing x using the neighborhood structure N_k.
      2. Local search phase: Apply a local search method starting from x' to obtain a new solution x''.
      3. If x'' is better than x_best, update x_best = x'' and set x = x''.
      4. If x'' is better than x, set x = x'' and k = 1; otherwise, set k = k + 1.
3. Return the best solution found x_best.

### Data Structures

- Set of neighborhood structures N_k, k = 1, ..., k_max: A set of predefined neighborhood structures ordered by increasing size or complexity.
- Current solution x: The current solution being explored during the search process.
- Best solution x_best: The best solution found so far during the search process.

### Parameters

- k_max: The maximum number of neighborhood structures used in the search process.
- Stopping criterion: A condition that determines when the search process should terminate, such as a maximum number of iterations or a time limit.

## Considerations

### Advantages

- Ability to escape local optima by systematically changing the neighborhood structure during the search process.
- Flexibility in defining the set of neighborhood structures, allowing the algorithm to be adapted to different problem domains.
- Relatively simple to implement and can be easily combined with other local search techniques or metaheuristics.

### Disadvantages

- Performance depends on the choice of neighborhood structures and the order in which they are applied.
- May require problem-specific knowledge to define effective neighborhood structures.
- The search process can be computationally expensive, especially for large problem instances or complex neighborhood structures.

## Heuristics

### Defining Neighborhood Structures

- Use a diverse set of neighborhood structures that can effectively explore different regions of the solution space.
- Order the neighborhood structures by increasing size or complexity, allowing the algorithm to progressively intensify the search.
- Consider problem-specific knowledge when defining neighborhood structures to ensure they are effective for the given problem domain.

### Balancing Exploration and Exploitation

- Adjust the number of neighborhood structures (k_max) based on the problem size and complexity. Larger values of k_max allow for more extensive exploration but may increase computational time.
- Control the intensity of the local search phase to balance exploration and exploitation. A more intensive local search can improve solution quality but may limit the algorithm's ability to escape local optima.

### Incorporating Randomization

- Introduce randomization in the shaking phase to ensure diverse perturbations and avoid cyclic behavior.
- Consider using adaptive or self-adaptive mechanisms to dynamically adjust the perturbation strength based on the search progress.

### Hybridization

- Combine Variable Neighborhood Search with other metaheuristics or local search techniques to enhance its performance.
- Incorporate problem-specific heuristics or domain knowledge to guide the search process and improve solution quality.

### Termination Criteria

- Use a combination of termination criteria, such as a maximum number of iterations, a time limit, or a stagnation detection mechanism, to ensure a balance between solution quality and computational time.
- Consider implementing an early stopping mechanism based on the rate of improvement in the best solution found to avoid unnecessary computations when the search is unlikely to yield further improvements.

