# Hierarchical Bayesian Optimization Algorithm

## Name

Hierarchical Bayesian Optimization Algorithm (HBOA)

## Taxonomy

The Hierarchical Bayesian Optimization Algorithm is a sequential model-based optimization technique that falls under the broad category of Bayesian Optimization methods. It is closely related to other Bayesian Optimization techniques such as Gaussian Process Optimization and Tree-structured Parzen Estimator.

- Computational Intelligence
  - Stochastic Optimization
    - Bayesian Optimization
      - Hierarchical Bayesian Optimization Algorithm (HBOA)

## Strategy

### Surrogate Modeling

HBOA constructs a hierarchical surrogate model of the objective function using Gaussian Processes (GPs). The surrogate model is built using observed data points and updated iteratively as new data becomes available. The hierarchical structure allows for modeling functions with different levels of fidelity, enabling efficient optimization of expensive black-box functions.

### Acquisition Function

To guide the search process, HBOA employs an acquisition function that balances exploration and exploitation. The acquisition function is used to select the next point to evaluate based on the surrogate model's predictions and uncertainties. Common choices for the acquisition function include Expected Improvement, Upper Confidence Bound, and Probability of Improvement.

### Hierarchical Search

HBOA leverages the hierarchical structure of the surrogate model to perform a multi-level search. It starts by exploring the search space at a coarse level using low-fidelity models and gradually refines the search using higher-fidelity models in promising regions. This approach allows for efficient allocation of computational resources and faster convergence to the optimal solution.

## Procedure
### Data Structures
- Search Space: A hierarchical structure representing the search space, where each level corresponds to a different level of abstraction or granularity.
- Gaussian Process: A probabilistic model used to model the objective function at each level of the hierarchy.
- Acquisition Function: A function that balances exploration and exploitation to guide the search process.

### Parameters
- Number of Levels: The number of levels in the hierarchical search space.
- Number of Iterations: The maximum number of iterations to run the algorithm at each level.
- Initial Points: The number of initial points to evaluate at each level before starting the optimization process.
- Kernel Function: The covariance function used in the Gaussian Process model.
- Acquisition Function Type: The type of acquisition function to use (e.g., Expected Improvement, Upper Confidence Bound).

### Steps
1. Initialize the hierarchical search space
   1. Define the number of levels and the corresponding search space at each level.
2. For each level in the hierarchy, starting from the highest level:
   1. Initialize the Gaussian Process model
      1. Select the initial points to evaluate at the current level.
      2. Evaluate the objective function at the selected points.
      3. Fit the Gaussian Process model to the evaluated points.
   2. For each iteration at the current level:
      1. Optimize the acquisition function
         1. Find the point that maximizes the acquisition function based on the current Gaussian Process model.
      2. Evaluate the objective function at the selected point
         1. Evaluate the objective function at the point that maximizes the acquisition function.
         2. Add the evaluated point and its objective value to the set of evaluated points.
      3. Update the Gaussian Process model
         1. Refit the Gaussian Process model to the updated set of evaluated points.
   3. If the current level is not the lowest level:
      1. Refine the search space
         1. Use the results from the current level to refine the search space for the next lower level.
         2. Define the refined search space for the next level based on the most promising regions identified at the current level.
   4. If the current level is the lowest level:
      1. Return the best solution found at the lowest level.

Note: The specific implementation details of the Hierarchical Bayesian Optimization Algorithm may vary depending on the problem domain and the chosen acquisition function and kernel function. The procedure outlined above provides a general framework for the algorithm.

### Data Structures

- Hierarchical Surrogate Model: A collection of Gaussian Process models at different fidelity levels.
- Acquisition Function: A function that assigns a value to each candidate point based on the surrogate model's predictions and uncertainties.
- Candidate Points: A set of potential points to evaluate next, sampled from the search space.

### Parameters

- Number of Fidelity Levels: The number of levels in the hierarchical surrogate model.
- Initial Data Points: The number of initial data points to collect at each fidelity level.
- Acquisition Function Type: The type of acquisition function to use (e.g., Expected Improvement, Upper Confidence Bound).
- Stopping Criteria: The conditions for terminating the optimization process (e.g., maximum number of iterations, convergence threshold).

## Considerations

### Advantages

- Efficient handling of expensive black-box functions by leveraging hierarchical surrogate models.
- Ability to incorporate multiple fidelity levels, enabling faster convergence and reduced computational cost.
- Balances exploration and exploitation through the use of acquisition functions.

### Disadvantages

- Requires careful selection of the number of fidelity levels and initial data points.
- The performance of HBOA depends on the quality of the surrogate model and the choice of acquisition function.
- May struggle with high-dimensional search spaces or highly multimodal objective functions.

## Heuristics

### Number of Fidelity Levels

- Start with a small number of fidelity levels (e.g., 2-3) and increase if necessary.
- Consider the trade-off between computational cost and model accuracy when selecting the number of levels.

### Initial Data Points

- Collect enough initial data points to provide a reasonable coverage of the search space at each fidelity level.
- Use design of experiments techniques (e.g., Latin Hypercube Sampling) to generate initial data points.

### Acquisition Function Selection

- Expected Improvement is a popular choice for balancing exploration and exploitation.
- Upper Confidence Bound is suitable for problems with noisy objective functions.
- Probability of Improvement can be used when a target value for the objective function is known.

### Stopping Criteria

- Set a maximum number of iterations based on the available computational budget.
- Define a convergence threshold based on the improvement in the objective function value over a certain number of iterations.
- Consider the diminishing returns in performance improvement when deciding when to stop the optimization process.


