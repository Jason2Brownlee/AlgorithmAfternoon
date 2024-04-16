# Factorized Distribution Algorithm

## Name

Factorized Distribution Algorithm (FDA)

## Taxonomy

The Factorized Distribution Algorithm is a probabilistic model-building evolutionary algorithm that belongs to the field of Estimation of Distribution Algorithms (EDAs) within the broader context of Evolutionary Computation and Optimization.

- Computational Intelligence
  - Evolutionary Computation
    - Evolutionary Algorithms
      - Estimation of Distribution Algorithms (EDAs)
        - Factorized Distribution Algorithm (FDA)

## Strategy

The Factorized Distribution Algorithm operates by iteratively updating a probabilistic model of promising solutions based on the best individuals in the current population. This model captures the dependencies between variables using a factorized representation, allowing for a more accurate and efficient exploration of the search space.

### Probabilistic Modeling

At each iteration, FDA constructs a probabilistic model by estimating the joint probability distribution of the selected individuals. This model factorizes the distribution into a product of marginal and conditional probabilities, capturing the dependencies between variables. The factorization is typically represented using a graphical model, such as a Bayesian network or a Markov random field.

### Sampling and Selection

Once the probabilistic model is built, FDA samples a new population of individuals from this model. The sampling process takes into account the learned dependencies between variables, generating offspring that inherit the promising patterns found in the selected parents. The generated individuals are then evaluated based on the problem-specific fitness function.

### Model Updating and Iteration

After evaluating the new individuals, FDA selects the best ones to update the probabilistic model for the next iteration. This selection process aims to gradually shift the model towards regions of the search space that contain high-quality solutions. The algorithm iterates until a termination criterion is met, such as reaching a maximum number of generations or finding a satisfactory solution.

## Procedure

1. Initialize:
   1. Set the population size (N), the selection size (S), and the maximum number of generations (G).
   2. Generate an initial population of N individuals randomly.
2. Evaluate the fitness of each individual in the population.
3. While the termination criterion is not met, repeat:
   1. Select S individuals from the population based on their fitness.
   2. Build a probabilistic model of the selected individuals:
      1. Estimate the joint probability distribution of the selected individuals.
      2. Factorize the distribution into a product of marginal and conditional probabilities.
      3. Represent the factorization using a graphical model (e.g., Bayesian network or Markov random field).
   3. Sample N new individuals from the probabilistic model.
   4. Evaluate the fitness of each new individual.
   5. Replace the current population with the new individuals.
   6. Increment the generation counter.
4. Return the best individual found during the search.

### Data Structures

- Population: An array of N individuals, each representing a candidate solution to the problem.
- Probabilistic Model: A graphical model (e.g., Bayesian network or Markov random field) that factorizes the joint probability distribution of the selected individuals.

### Parameters

- Population Size (N): The number of individuals in the population.
- Selection Size (S): The number of individuals selected to build the probabilistic model.
- Maximum Number of Generations (G): The termination criterion based on the number of iterations.

## Considerations

### Advantages

- Captures dependencies between variables, leading to a more accurate modeling of promising regions in the search space.
- Reduces the risk of premature convergence by maintaining diversity through probabilistic modeling.
- Adapts the search to the problem structure by learning and exploiting the variable interactions.

### Disadvantages

- The computational complexity of building and sampling from the probabilistic model can be high, especially for problems with a large number of variables and complex dependencies.
- The performance of FDA depends on the quality of the probabilistic model, which may require careful design and tuning.
- The algorithm may struggle with problems that have highly multimodal or deceptive fitness landscapes, as it relies on the assumption that good solutions share common patterns.

## Heuristics

### Population Size

- Start with a population size that is at least 10 times the number of variables in the problem.
- Increase the population size for problems with high dimensionality or complex dependencies between variables.
- Consider the trade-off between exploration and computational efficiency when setting the population size.

### Selection Size

- Choose a selection size that balances the need for maintaining diversity and focusing on promising regions.
- A common heuristic is to select around 50% of the population size.
- Experiment with different selection sizes to find the best value for the specific problem.

### Probabilistic Model Building

- Use a graphical model that can effectively capture the dependencies between variables, such as a Bayesian network or a Markov random field.
- Consider the complexity of the model and the computational cost of learning and sampling from it.
- If the problem has a known or assumed structure, incorporate this knowledge into the design of the probabilistic model.

### Termination Criterion

- Set a maximum number of generations based on the available computational resources and the problem complexity.
- Consider using additional termination criteria, such as convergence detection or a minimum fitness threshold.
- Monitor the progress of the algorithm and adjust the termination criterion if necessary.

### Hybridization

- Consider combining FDA with local search techniques to refine the solutions generated by the probabilistic model.
- Incorporate domain-specific heuristics or operators to enhance the search process and improve the quality of the solutions.
- Experiment with different hybridization strategies and assess their impact on the algorithm's performance.