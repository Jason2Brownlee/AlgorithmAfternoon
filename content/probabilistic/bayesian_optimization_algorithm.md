# Bayesian Optimization Algorithm

## Name
Bayesian Optimization Algorithm (BOA), Bayesian Optimization

## Taxonomy
Bayesian Optimization is a global optimization technique that belongs to the field of Computational Intelligence and is closely related to Gaussian Process Optimization and Efficient Global Optimization. It is a derivative-free, model-based optimization approach that is particularly well-suited for expensive-to-evaluate, black-box objective functions.

- Computational Intelligence
  - Stochastic Optimization
    - Derivative-Free Optimization
      - Model-Based Optimization
        - Bayesian Optimization
          - Gaussian Process Optimization
          - Efficient Global Optimization

## Strategy
Bayesian Optimization constructs a probabilistic surrogate model of the objective function, typically using Gaussian Processes, and sequentially updates this model as new observations are made. The next point to evaluate is chosen by maximizing an acquisition function, which balances exploration (sampling from areas of high uncertainty) and exploitation (sampling areas likely to offer improvement over the current best observation).

The algorithm starts with an initial set of observations, which are used to construct the surrogate model. The acquisition function is then maximized to determine the next point to evaluate. The surrogate model is updated with the new observation, and the process is repeated until a specified termination criterion is met, such as reaching a maximum number of iterations or achieving a satisfactory objective value.

Bayesian Optimization is particularly effective when the objective function is expensive to evaluate, as it aims to minimize the number of evaluations required to find the global optimum. The surrogate model allows for efficient exploration of the search space, while the acquisition function guides the search towards promising regions.

### Surrogate Model
The surrogate model is a probabilistic approximation of the objective function, which is used to guide the search process. Gaussian Processes (GPs) are commonly used as the surrogate model in Bayesian Optimization due to their flexibility and ability to model uncertainty. GPs define a prior distribution over functions, which is updated as new observations are made, resulting in a posterior distribution that captures the model's uncertainty about the objective function.

### Acquisition Function
The acquisition function is a criterion used to determine the next point to evaluate based on the surrogate model. It balances the trade-off between exploration and exploitation, aiming to maximize the expected improvement in the objective function. Common acquisition functions include Expected Improvement (EI), Upper Confidence Bound (UCB), and Probability of Improvement (PI). The choice of acquisition function depends on the specific problem and the desired balance between exploration and exploitation.

## Procedure
Data Structures:
- `X`: Set of input observations
- `y`: Set of corresponding objective function values
- `M`: Surrogate model (typically a Gaussian Process)
- `α`: Acquisition function

Parameters:
- `n_init`: Number of initial observations
- `n_iter`: Number of optimization iterations
- `xi`: Exploration-exploitation trade-off parameter

Steps:
1. Initialize:
   1. Generate `n_init` initial observations by randomly sampling points from the input space
   2. Evaluate the objective function at the initial points and store the results in `X` and `y`
2. Update the surrogate model `M` using the current observations `X` and `y`
3. For `i` = 1 to `n_iter`:
   1. Maximize the acquisition function `α` to determine the next point `x_next` to evaluate:
      `x_next` = argmax(`α`(`x`))
   2. Evaluate the objective function at `x_next` and append the result to `X` and `y`
   3. Update the surrogate model `M` with the new observation
4. Return the best observed point and its corresponding objective function value

## Considerations
Advantages:
- Efficient for expensive-to-evaluate objective functions, as it minimizes the number of function evaluations required
- Handles black-box optimization problems, where the objective function is unknown or not differentiable
- Provides a balance between exploration and exploitation, allowing for effective search of the global optimum

Disadvantages:
- The performance of the algorithm depends on the choice of surrogate model and acquisition function
- The computational complexity of fitting the surrogate model and maximizing the acquisition function can be high, especially for high-dimensional problems
- The algorithm may struggle with highly multimodal or non-smooth objective functions, as the surrogate model may not capture the function's complexity accurately

## Heuristics
### Initialization
- Use prior knowledge about the problem domain to guide the initial sampling, if available
- If no prior knowledge is available, use random sampling or space-filling designs (e.g., Latin Hypercube Sampling) to generate the initial observations

### Surrogate Model
- Gaussian Processes are a common choice for the surrogate model due to their flexibility and ability to model uncertainty
- Consider using Matérn kernels for the Gaussian Process, as they can handle non-smooth functions better than the standard Squared Exponential kernel
- Optimize the hyperparameters of the surrogate model using techniques like maximum likelihood estimation or cross-validation

### Acquisition Function
- Expected Improvement (EI) is a popular choice for the acquisition function, as it provides a good balance between exploration and exploitation
- Upper Confidence Bound (UCB) can be used for more exploration-oriented search, while Probability of Improvement (PI) can be used for more exploitation-oriented search
- Adjust the exploration-exploitation trade-off parameter `xi` based on the problem characteristics and the desired balance

### Termination Criteria
- Set a maximum number of iterations `n_iter` based on the available computational budget and the complexity of the problem
- Consider using an early stopping criterion based on the convergence of the surrogate model or the improvement in the objective function
- Define a minimum improvement threshold to avoid wasting evaluations on minor improvements

### Parallelization
- Bayesian Optimization can be parallelized by evaluating multiple points simultaneously at each iteration
- Consider using batch acquisition functions, such as the qExpected Improvement (qEI), to select multiple points for parallel evaluation
- Ensure that the surrogate model is updated with all the new observations before proceeding to the next iteration
