# Compact Genetic Algorithm

## Name

Compact Genetic Algorithm (cGA)

## Taxonomy

The Compact Genetic Algorithm is a variation of the standard Genetic Algorithm, belonging to the field of Evolutionary Computation, which is a subfield of Computational Intelligence. It is closely related to other population-based optimization algorithms such as Estimation of Distribution Algorithms (EDAs) and Probabilistic Model-Building Genetic Algorithms (PMBGAs).

- Computational Intelligence
  - Evolutionary Computation
    - Evolutionary Algorithms
      - Genetic Algorithms
        - Compact Genetic Algorithm

## Strategy

The Compact Genetic Algorithm operates on a probabilistic model of the population rather than maintaining an explicit population of individuals. This model is represented by a probability vector, where each element corresponds to the probability of a specific gene (or bit) being present in an individual.

### Probability Vector Update

At each iteration, the algorithm generates two candidate solutions by sampling from the probability vector. These solutions are then evaluated using the objective function, and their fitness values are compared. Based on the comparison, the probability vector is updated to favor the bits of the better solution. This update is performed using a simple frequency-based rule, where the probability of each bit is incremented or decremented by a small step size.

### Convergence and Termination

The process of generating candidate solutions, evaluating their fitness, and updating the probability vector continues until convergence is reached or a maximum number of iterations is exceeded. Convergence is typically determined by monitoring the entropy of the probability vector, which measures the uncertainty or diversity of the population. As the algorithm progresses, the entropy decreases, indicating that the population is becoming more homogeneous and converging towards a specific solution.

## Procedure

### Data Structures

- `probability_vector`: A list of probabilities, where each element represents the probability of a specific bit being present in an individual.
- `best_solution`: The best solution found so far during the optimization process.
- `best_fitness`: The fitness value of the best solution found so far.

### Parameters

- `population_size`: The virtual population size used to update the probability vector.
- `max_iterations`: The maximum number of iterations allowed before termination.
- `step_size`: The step size used to update the probability vector based on the comparison of candidate solutions.

### Pseudocode

1. Initialize the `probability_vector` with values of 0.5 for each bit.
2. Initialize `best_solution` and `best_fitness` to None.
3. For each iteration until `max_iterations` is reached or convergence is detected:
   1. Generate two candidate solutions, `solution1` and `solution2`, by sampling from the `probability_vector`.
   2. Evaluate the fitness of `solution1` and `solution2` using the objective function.
   3. If the fitness of `solution1` is better than `solution2`:
      1. Update the `probability_vector` by incrementing the probabilities of the bits in `solution1` and decrementing the probabilities of the bits in `solution2` using the `step_size`.
   4. Else:
      1. Update the `probability_vector` by incrementing the probabilities of the bits in `solution2` and decrementing the probabilities of the bits in `solution1` using the `step_size`.
   5. If the fitness of the better solution is better than `best_fitness`:
      1. Update `best_solution` and `best_fitness` with the better solution and its fitness.
4. Return `best_solution` and `best_fitness`.

## Considerations

### Advantages

- Memory efficiency: The Compact Genetic Algorithm requires significantly less memory compared to traditional Genetic Algorithms since it maintains only a probability vector instead of an explicit population.
- Faster convergence: By focusing on the probabilistic model of the population, the algorithm can converge faster towards promising regions of the search space.
- Adaptive search: The probability vector update mechanism allows the algorithm to adapt its search based on the feedback from the objective function, leading to a more targeted exploration of the search space.

### Disadvantages

- Limited diversity: As the algorithm converges, the diversity of the virtual population decreases, which may lead to premature convergence and difficulty in escaping local optima.
- Sensitivity to step size: The performance of the algorithm is sensitive to the choice of the step size parameter. An inappropriate step size can lead to slow convergence or premature convergence.
- Lack of explicit population: The absence of an explicit population may limit the algorithm's ability to maintain and exploit diverse solutions, especially in multimodal optimization problems.

## Heuristics

### Population Size

- The virtual population size should be chosen based on the problem complexity and the desired balance between exploration and exploitation.
- Larger population sizes can help maintain diversity and improve exploration but may slow down convergence.
- Smaller population sizes can accelerate convergence but may increase the risk of premature convergence.

### Step Size

- The step size determines the magnitude of updates to the probability vector based on the comparison of candidate solutions.
- A larger step size can lead to faster convergence but may cause the algorithm to overshoot the optimal solution.
- A smaller step size allows for more gradual updates and a finer-grained search but may slow down convergence.
- The step size can be adapted during the optimization process based on the progress of the algorithm, e.g., reducing the step size as the algorithm approaches convergence.

### Convergence Criteria

- Convergence can be determined by monitoring the entropy of the probability vector, which measures the uncertainty or diversity of the virtual population.
- A threshold can be set for the entropy, below which the algorithm is considered to have converged.
- Additionally, a maximum number of iterations can be specified to terminate the algorithm if convergence is not reached within a certain number of iterations.

### Initialization

- The probability vector is typically initialized with values of 0.5 for each bit, representing an unbiased starting point.
- In some cases, prior knowledge about the problem domain can be used to initialize the probability vector with more informative values, guiding the search towards promising regions.

### Elitism

- Elitism can be incorporated into the Compact Genetic Algorithm by always preserving the best solution found so far.
- This can be achieved by updating the best solution and its fitness whenever a better solution is found during the optimization process.
- Elitism helps prevent the loss of good solutions and ensures that the algorithm always retains the best solution discovered.

