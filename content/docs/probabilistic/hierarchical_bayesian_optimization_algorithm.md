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

1. Initialize the hierarchical surrogate model with initial data points.
   1.1. Define the hierarchy of fidelity levels for the surrogate model.
   1.2. Collect initial data points at different fidelity levels.
   1.3. Fit Gaussian Process models to the data points at each fidelity level.

2. While stopping criteria not met:
   2.1. Select the next point to evaluate using the acquisition function.
       2.1.1. Compute the acquisition function values for candidate points at each fidelity level.
       2.1.2. Choose the point with the highest acquisition function value.
   2.2. Evaluate the objective function at the selected point.
   2.3. Update the hierarchical surrogate model with the new data point.
       2.3.1. Incorporate the new data point into the corresponding fidelity level.
       2.3.2. Update the Gaussian Process models at each fidelity level.

3. Return the best solution found.

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


