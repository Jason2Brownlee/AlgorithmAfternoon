# Covariance Matrix Adaptation Evolution Strategy

## Name

Covariance Matrix Adaptation Evolution Strategy (CMA-ES)

## Taxonomy

CMA-ES is a stochastic optimization algorithm that falls under the category of Evolutionary Algorithms, which are a subset of Computational Intelligence and Biologically Inspired Computation. It is closely related to other Evolution Strategies, such as (1+1)-ES and (μ/μ_w, λ)-ES.

- Computational Intelligence
  - Biologically Inspired Computation
    - Evolutionary Computation
      - Evolutionary Algorithms
        - Evolution Strategies
          - Covariance Matrix Adaptation Evolution Strategy (CMA-ES)

## Strategy

### Adaptation of the Covariance Matrix

CMA-ES maintains a multivariate normal distribution as a search distribution, which is updated iteratively to adapt to the landscape of the objective function. The covariance matrix of this distribution represents the shape and orientation of the search distribution, allowing CMA-ES to efficiently explore promising regions of the search space.

### Rank-Based Selection

In each iteration, CMA-ES samples a population of candidate solutions from the current search distribution. These solutions are then evaluated using the objective function, and a subset of the best solutions is selected based on their rank. This rank-based selection mechanism emphasizes the relative performance of solutions rather than their absolute fitness values, making CMA-ES robust to different scales and transformations of the objective function.

### Cumulative Step-Size Adaptation

CMA-ES employs a step-size control mechanism called cumulative step-size adaptation, which adjusts the overall scale of the search distribution based on the cumulative path of successful mutations. This adaptation enables CMA-ES to automatically adjust the step-size to the local characteristics of the objective function, leading to efficient convergence.

## Procedure

### Data Structures

- `mean`: The mean vector of the search distribution
- `covariance`: The covariance matrix of the search distribution
- `stepSize`: The global step-size of the search distribution
- `populationSize`: The number of candidate solutions sampled in each iteration
- `muEffective`: The effective number of selected solutions used for updating the search distribution

### Parameters

- `populationSize`: The size of the population sampled in each iteration (default: 4 + floor(3 * log(dimensionality)))
- `muRatio`: The ratio of selected solutions used for updating the search distribution (default: 0.5)
- `cumulationFactor`: The weight of the cumulative path for step-size adaptation (default: (muEffective + 2) / (dimensionality + muEffective + 5))
- `dampFactor`: The damping factor for step-size adaptation (default: 1 + 2 * max(0, sqrt((muEffective - 1) / (dimensionality + 1)) - 1) + cumulationFactor)

### Initialization

1. Initialize `mean` to a random point in the search space
2. Initialize `covariance` to an identity matrix
3. Initialize `stepSize` to a suitable value based on the search space bounds
4. Compute `populationSize` and `muEffective` based on the dimensionality and `muRatio`
5. Compute `cumulationFactor` and `dampFactor` based on `muEffective` and the dimensionality

### Main Loop

1. Sample a population of `populationSize` candidate solutions from a multivariate normal distribution with `mean` and `covariance * (stepSize^2)`
2. Evaluate the fitness of each candidate solution using the objective function
3. Select the best `muEffective` solutions based on their rank
4. Update `mean` to the weighted average of the selected solutions
5. Update `covariance` based on the selected solutions and the cumulative path of successful mutations
6. Update `stepSize` based on the cumulative path of successful mutations and the `dampFactor`
7. Check termination criteria (e.g., maximum iterations, fitness threshold)
8. If termination criteria are not met, go to step 1

## Considerations

### Advantages

- Invariance properties: CMA-ES is invariant to rank-preserving transformations of the objective function and to rotations and translations of the search space, making it robust and applicable to a wide range of optimization problems.
- Self-adaptation: CMA-ES automatically adapts the shape and scale of the search distribution to the local characteristics of the objective function, eliminating the need for manual parameter tuning.
- Efficient on ill-conditioned and non-separable problems: CMA-ES performs well on problems with ill-conditioned and non-separable search landscapes, where other optimization algorithms may struggle.

### Disadvantages

- Computationally expensive: CMA-ES requires a significant number of objective function evaluations, which can be costly for high-dimensional problems or expensive objective functions.
- Limited theoretical convergence guarantees: While CMA-ES has been shown to perform well empirically, its theoretical convergence properties are not as well-established as some other optimization algorithms.
- Sensitive to noisy objective functions: CMA-ES may struggle with objective functions that are subject to significant noise, as the rank-based selection mechanism can be misled by noisy fitness evaluations.

## Heuristics

### Population Size

- For problems with a low dimensionality (e.g., less than 10), consider using a larger population size than the default to encourage exploration.
- For problems with a high dimensionality (e.g., more than 100), consider using a smaller population size than the default to reduce computational overhead.

### Initial Step-Size

- If the search space bounds are known, set the initial step-size to approximately one-third of the range of the search space in each dimension.
- If the search space bounds are unknown, consider using a small initial step-size (e.g., 0.1) and rely on the step-size adaptation mechanism to adjust it appropriately.

### Termination Criteria

- Use a maximum number of iterations or function evaluations to prevent excessive computation time.
- Monitor the best fitness value found so far and terminate if it does not improve significantly over a certain number of iterations.
- Consider terminating if the step-size falls below a certain threshold, indicating that the search has converged to a local optimum.

### Restarts

- If CMA-ES converges to a suboptimal solution, consider restarting the algorithm from a different initial point to explore other regions of the search space.
- Employ a multi-start strategy, running CMA-ES multiple times with different initial conditions and selecting the best solution found across all runs.

### Hybrid Approaches

- Consider combining CMA-ES with local search techniques, such as Nelder-Mead or BFGS, to refine solutions and accelerate convergence in the final stages of optimization.
- Use CMA-ES as a global search method to identify promising regions of the search space, and then apply a local search method to efficiently locate the exact optimum within those regions.

