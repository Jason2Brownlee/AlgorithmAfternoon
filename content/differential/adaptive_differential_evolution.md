# Adaptive Differential Evolution

## Name
Adaptive Differential Evolution (ADE), Self-Adaptive Differential Evolution, Adaptive DE, jDE (self-adaptive DE variant)

## Taxonomy
Adaptive Differential Evolution is a stochastic optimization technique that belongs to the family of Evolutionary Algorithms, which are part of the broader field of Computational Intelligence and Biologically Inspired Computation. It is an extension of the original Differential Evolution (DE) algorithm that incorporates self-adaptation mechanisms.

- Computational Intelligence
  - Biologically Inspired Computation
    - Evolutionary Algorithms
      - Evolutionary Strategies
        - Differential Evolution (DE)
          - Adaptive Differential Evolution (ADE)

## Strategy
Adaptive Differential Evolution builds upon the basic Differential Evolution algorithm by introducing self-adaptation mechanisms for the control parameters, namely the scale factor (F) and the crossover rate (CR). These parameters are critical to the performance of DE, and their optimal values are problem-dependent. In ADE, each individual in the population is associated with its own set of control parameters, which are updated based on their success in generating improved solutions.

The main idea behind the adaptation strategy is to reward successful parameter values and propagate them to the next generation. This is achieved by inheriting the control parameters from the parent vectors that successfully produce offspring better than the current target vector. Over time, the population learns to adapt its control parameters to the specific problem at hand, leading to more efficient exploration and exploitation of the search space.

The adaptation mechanism in ADE can be implemented in various ways, such as using a simple inheritance scheme, a weighted average of successful parameter values, or more sophisticated learning strategies. The specific adaptation rules may vary depending on the variant of ADE being used.

## Procedure
Data Structures:
- Population: A set of candidate solutions, each represented as a vector of real numbers.
- Control Parameters: Each individual has its own set of control parameters (F and CR).

Parameters:
- Population Size (NP): The number of individuals in the population.
- Problem Dimension (D): The number of variables in the optimization problem.
- Lower and Upper Bounds: The minimum and maximum allowed values for each variable.
- Termination Criteria: Maximum number of generations or a convergence threshold.

Procedure:
1. Initialization:
   1. Generate an initial population of NP individuals with random positions within the specified bounds.
   2. Initialize the control parameters (F and CR) for each individual, either with fixed values or randomly within predefined ranges.

2. Evaluation:
   1. Evaluate the fitness (objective function value) of each individual in the population.

3. Mutation:
   1. For each target vector in the population:
      1. Select three distinct individuals randomly from the population.
      2. Calculate the mutant vector using the DE/rand/1 strategy: V = X[r1] + F * (X[r2] - X[r3]), where X[r1], X[r2], and X[r3] are the selected individuals, and F is the scale factor.

4. Crossover:
   1. For each target vector and its corresponding mutant vector:
      1. Generate a trial vector by copying elements from either the target vector or the mutant vector based on the crossover rate (CR).

5. Selection:
   1. For each target vector and its corresponding trial vector:
      1. Evaluate the fitness of the trial vector.
      2. If the trial vector is better than the target vector, replace the target vector with the trial vector in the population.
      3. If the trial vector successfully replaces the target vector, inherit the control parameters (F and CR) from the trial vector to the next generation.

6. Adaptation:
   1. Update the control parameters (F and CR) of each individual based on the adaptation rules of the specific ADE variant being used.

7. Termination:
   1. If the termination criteria are met, stop the algorithm and return the best solution found.
   2. Otherwise, go back to step 3 (Mutation).

## Considerations
Advantages:
- Self-adaptation of control parameters, reducing the need for manual tuning.
- Improved robustness and performance compared to the original DE algorithm.
- Ability to adapt to the characteristics of the problem during the optimization process.

Disadvantages:
- Increased computational complexity due to the adaptation mechanism.
- The effectiveness of the adaptation rules may depend on the specific problem and the chosen ADE variant.
- The self-adaptation process may require additional function evaluations, which can be costly for expensive objective functions.

## Heuristics
Population Size:
- A larger population size can improve the exploration of the search space but increases the computational cost.
- As a general guideline, consider using a population size between 5D and 10D, where D is the problem dimension.

Mutation Strategy:
- The DE/rand/1 strategy is commonly used, but other strategies like DE/best/1 or DE/current-to-best/1 can be employed depending on the problem characteristics.
- Experiment with different mutation strategies to find the most suitable one for the problem at hand.

Initial Control Parameter Ranges:
- The initial ranges for F and CR can be set based on common values found in the literature, such as F ∈ [0.5, 1.0] and CR ∈ [0.8, 1.0].
- Alternatively, use a wider range to allow more diversity in the initial population, e.g., F ∈ [0.1, 1.0] and CR ∈ [0.1, 1.0].

Adaptation Rules:
- Simple inheritance of control parameters from successful trial vectors is a straightforward and effective adaptation rule.
- More advanced adaptation strategies, such as weighted averages or learning-based approaches, can be considered for specific problem types.

Termination Criteria:
- Define a maximum number of generations based on the available computational resources and the problem complexity.
- Alternatively, use a convergence threshold based on the improvement of the best fitness value over a certain number of generations.

Constraint Handling:
- When dealing with constrained optimization problems, incorporate constraint handling techniques like penalty functions or repair mechanisms.
- Ensure that the adaptation rules consider the feasibility of the solutions in addition to their fitness values.

Hybrid Approaches:
- Consider combining ADE with local search techniques or other optimization algorithms to further improve the solution quality and convergence speed.
- Hybridization can be particularly beneficial for problems with complex landscapes or multiple local optima.

Parameter Control:
- While ADE automates the adaptation of F and CR, other parameters like the population size or the mutation strategy may still require manual tuning.
- Conduct parameter sensitivity analysis to understand the impact of these parameters on the algorithm's performance.

Parallelization:
- ADE is well-suited for parallelization due to the independent nature of the mutation and crossover operations.
- Implement parallel versions of ADE to leverage multi-core processors or distributed computing environments for faster execution.

Continuous Learning:
- Regularly monitor the performance of ADE on the problem at hand and analyze the adapted control parameter values.
- Use this information to gain insights into the problem characteristics and refine the adaptation rules or hybridization strategies accordingly.
