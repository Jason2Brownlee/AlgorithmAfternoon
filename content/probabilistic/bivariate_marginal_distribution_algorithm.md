# Bivariate Marginal Distribution Algorithm

## Name
Bivariate Marginal Distribution Algorithm (BMDA)

## Taxonomy
The Bivariate Marginal Distribution Algorithm is a type of Estimation of Distribution Algorithm (EDA), which belongs to the field of Evolutionary Computation, a subfield of Computational Intelligence. EDAs are closely related to other Evolutionary Algorithms such as Genetic Algorithms and Evolution Strategies.

- Computational Intelligence
  - Evolutionary Computation
    - Evolutionary Algorithms
      - Genetic Algorithms
      - Evolution Strategies
      - Estimation of Distribution Algorithms
        - Univariate Marginal Distribution Algorithm
        - Bivariate Marginal Distribution Algorithm
        - Multivariate Marginal Distribution Algorithm

## Strategy
The Bivariate Marginal Distribution Algorithm is an optimization technique that learns a probabilistic model of promising solutions by estimating a bivariate probability distribution from a population of candidate solutions. The algorithm iteratively samples new candidate solutions from the learned model, selects the best solutions, and updates the model based on the selected solutions.

The key idea behind BMDA is to capture the pairwise dependencies between variables in the problem domain. By modeling the bivariate marginal distributions, BMDA can exploit the interactions between variables and generate new solutions that combine the promising features of the selected solutions.

### Probabilistic Modeling
BMDA estimates a bivariate probability distribution for each pair of variables in the problem domain. The bivariate distributions capture the pairwise dependencies between variables and allow the algorithm to generate new solutions that inherit the promising combinations of variable values from the selected solutions.

### Sampling and Selection
In each iteration, BMDA samples a new population of candidate solutions from the learned bivariate distributions. The sampling process generates solutions that combine the promising features of the selected solutions from the previous iteration. The algorithm then evaluates the fitness of the new solutions and selects the best ones based on their fitness values.

### Model Update
After selecting the best solutions, BMDA updates the bivariate probability distributions based on the selected solutions. The update process adjusts the distributions to increase the probability of generating solutions similar to the selected ones in the next iteration. This iterative process of sampling, selection, and model update continues until a termination criterion is met.

## Procedure
### Data Structures
- Population: A set of candidate solutions.
- Bivariate Distributions: A set of probability distributions, one for each pair of variables in the problem domain.

### Parameters
- Population Size: The number of candidate solutions in the population.
- Selection Size: The number of solutions selected in each iteration.
- Maximum Iterations: The maximum number of iterations allowed.

### Procedure Steps
1. Initialize the population with random candidate solutions.
2. Evaluate the fitness of each solution in the population.
3. While the termination criterion is not met:
   1. Select the best solutions from the population based on their fitness values.
   2. Estimate the bivariate probability distributions from the selected solutions.
   3. Sample a new population of candidate solutions from the bivariate distributions.
   4. Evaluate the fitness of each new solution.
   5. Replace the old population with the new population.
4. Return the best solution found.

## Considerations
### Advantages
- Captures pairwise dependencies between variables, allowing for more effective exploration of the search space.
- Generates new solutions by combining promising features of selected solutions, leading to faster convergence.
- Suitable for problems with complex variable interactions and multimodal fitness landscapes.

### Disadvantages
- Higher computational complexity compared to univariate EDAs due to the estimation of bivariate distributions.
- May struggle with problems that have higher-order dependencies beyond pairwise interactions.
- The performance may be sensitive to the choice of population size and selection size parameters.

## Heuristics
### Population Size
- Start with a population size that is at least 10 times the number of variables in the problem.
- Increase the population size for problems with high dimensionality or complex fitness landscapes.
- Larger population sizes can improve exploration but may slow down convergence.

### Selection Size
- Choose a selection size that is a fraction of the population size, typically between 10% and 50%.
- Larger selection sizes can lead to faster convergence but may increase the risk of premature convergence.
- Smaller selection sizes can maintain diversity but may slow down convergence.

### Termination Criterion
- Set a maximum number of iterations based on the problem complexity and available computational resources.
- Use a convergence criterion based on the improvement of the best fitness value over a certain number of iterations.
- Consider a combination of maximum iterations and convergence criteria to balance exploration and exploitation.

### Handling Constraints
- Incorporate constraint handling techniques such as penalty functions or repair mechanisms to deal with infeasible solutions.
- Adjust the sampling process to generate solutions that satisfy the constraints.
- Use specialized operators or local search techniques to improve the feasibility of solutions.

### Hybridization
- Consider hybridizing BMDA with local search techniques to refine the solutions and improve local optimization.
- Incorporate domain-specific heuristics or problem-specific knowledge into the initialization, sampling, or selection processes.
- Combine BMDA with other optimization algorithms to leverage their strengths and overcome limitations.
