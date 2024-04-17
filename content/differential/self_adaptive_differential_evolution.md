# Self-adaptive Differential Evolution

## Name

Self-adaptive Differential Evolution (SaDE), Adaptive Differential Evolution, Parameter Adaptive Differential Evolution

## Taxonomy

Self-adaptive Differential Evolution is a stochastic optimization algorithm that belongs to the field of Evolutionary Computation, which is a subfield of Computational Intelligence. It is closely related to other Differential Evolution algorithms and Evolutionary Algorithms.

- Computational Intelligence
  - Biologically Inspired Computation
    - Evolutionary Computation
      - Evolutionary Algorithms
        - Differential Evolution
          - Self-adaptive Differential Evolution

## Strategy

### Mutation and Crossover

SaDE generates new candidate solutions by combining the current population members using mutation and crossover operations. The mutation strategy and associated control parameters are dynamically adapted during the optimization process based on their previous success rates. This self-adaptation mechanism allows the algorithm to automatically adjust its search behavior to the characteristics of the problem at hand.

### Selection

After generating new candidates, SaDE compares each new solution with its corresponding parent in the current population. If the new solution has a better fitness value, it replaces the parent in the next generation; otherwise, the parent is retained. This selection scheme ensures that the population quality improves over successive generations.

### Parameter Adaptation

SaDE maintains a set of mutation strategies and associated control parameters. The selection probabilities of these strategies are updated based on their success rates in generating improved solutions. Strategies that consistently produce better candidates are assigned higher probabilities, while less successful strategies are gradually phased out. This adaptation allows the algorithm to focus on the most effective search mechanisms for the given problem.

## Procedure

### Data Structures

- Population: An array of candidate solutions, where each solution is represented as a vector of decision variables.
- Strategy Pool: A collection of mutation strategies and their associated control parameters.
- Strategy Probabilities: An array storing the selection probabilities of each mutation strategy.
- Strategy Success Rates: An array keeping track of the success rates of each mutation strategy.

### Parameters

- Population Size: The number of candidate solutions in the population.
- Mutation Strategies: A set of predefined mutation strategies (e.g., "DE/rand/1", "DE/best/1", "DE/current-to-best/1").
- Crossover Probability: The probability of applying the crossover operation to generate new candidates.
- Scaling Factor Range: The range from which the scaling factor (F) values are drawn for each mutation strategy.
- Adaptation Interval: The number of generations between parameter adaptation steps.

### Main Loop

1. Initialize the population randomly within the search space bounds.
2. Initialize the strategy pool with predefined mutation strategies and their control parameters.
3. Set the initial selection probabilities for each strategy equally.
4. While the termination criteria are not met, do:
   1. For each individual in the population, do:
      1. Select a mutation strategy from the strategy pool based on their probabilities.
      2. Generate a new candidate solution using the selected strategy and its control parameters.
      3. Apply crossover between the current individual and the new candidate.
      4. Evaluate the fitness of the new candidate.
      5. If the new candidate is better than the current individual, replace it in the population.
      6. Update the success rate of the selected strategy.
   2. If the adaptation interval is reached, do:
      1. Update the selection probabilities of the strategies based on their success rates.
      2. Reset the strategy success rates.
5. Return the best solution found.

## Considerations

### Advantages

- Adaptability: SaDE automatically adapts its mutation strategies and control parameters to the problem characteristics, eliminating the need for manual tuning.
- Robustness: The self-adaptation mechanism makes SaDE more robust to the choice of initial parameter values and enables it to maintain good performance across a wide range of problems.
- Efficiency: By focusing on the most successful strategies, SaDE can converge faster and achieve better solutions compared to non-adaptive Differential Evolution algorithms.

### Disadvantages

- Increased Complexity: The self-adaptation mechanism introduces additional complexity to the algorithm, which may make it more difficult to understand and implement compared to standard Differential Evolution.
- Computational Overhead: Maintaining and updating the strategy probabilities and success rates incur some computational overhead, which may slow down the algorithm compared to non-adaptive variants.
- Parameter Sensitivity: Although SaDE is less sensitive to parameter settings than standard Differential Evolution, the performance may still be affected by the choice of adaptation interval and the initial strategy pool.

## Heuristics

### Population Size

- Start with a population size of 5 to 10 times the number of decision variables in the problem.
- For high-dimensional problems (100+ variables), consider increasing the population size to maintain diversity.

### Mutation Strategies

- Include a diverse set of mutation strategies in the initial pool, such as "DE/rand/1", "DE/best/1", and "DE/current-to-best/1".
- For problems with many local optima, prioritize strategies that promote exploration, such as "DE/rand/1".
- For problems with a strong global structure, prioritize strategies that exploit the best solutions, such as "DE/best/1".

### Crossover Probability

- Use a crossover probability in the range of 0.7 to 0.9 for most problems.
- For problems with strong variable dependencies, consider increasing the crossover probability to promote information exchange between solutions.

### Adaptation Interval

- Set the adaptation interval to a value between 5 and 20 generations, depending on the problem size and complexity.
- For fast-changing problems, use shorter adaptation intervals to allow quicker response to changes in the search landscape.
- For problems with a stable fitness landscape, use longer adaptation intervals to reduce the adaptation overhead.

### Scaling Factor Range

- Use a scaling factor range of [0.5, 1.0] as a default for most problems.
- For problems with a high degree of separability, consider reducing the lower bound of the range to encourage more local search.
- For problems with strong variable interactions, consider increasing the upper bound of the range to promote exploration.

