---
title: DE/best/1/z
---
# DE/best/1/z

## Name

DE/best/1/z, Differential Evolution "best/1" with optional external archive.

## Taxonomy

DE/best/1/z is a variation of the Differential Evolution (DE) algorithm, which belongs to the field of Evolutionary Computation, a subfield of Computational Intelligence. DE is closely related to other Evolutionary Algorithms, such as Genetic Algorithms and Evolution Strategies.

- Computational Intelligence
  - Biologically Inspired Computation
    - Evolutionary Computation
      - Evolutionary Algorithms
        - Differential Evolution (DE)
          - DE/best/1/z

## Strategy

DE/best/1/z follows the general Differential Evolution strategy of maintaining a population of candidate solutions and evolving them through a process of mutation, crossover, and selection. The key distinguishing feature of DE/best/1/z is its mutation strategy, which uses the best individual in the population as the base vector for mutation.

### Mutation

In the mutation step, DE/best/1/z creates a mutant vector by adding the weighted difference between two randomly selected population members to the best individual in the current population. This guides the search towards the most promising regions of the search space.

### Crossover

After mutation, a crossover operation is performed between the mutant vector and the corresponding target vector in the population. This introduces diversity and enables the exchange of information between solutions. DE/best/1/z employs the binomial crossover, where each dimension of the offspring vector is inherited from either the mutant vector or the target vector based on a crossover probability.

### Selection

The selection step determines whether the newly created offspring vector replaces the target vector in the population for the next generation. DE/best/1/z uses a greedy selection strategy, where the offspring vector replaces the target vector only if it has a better fitness value.

### External Archive (z)

DE/best/1/z incorporates an optional external archive, denoted by the "z" in its name. The archive stores the best solutions found during the search process. These archived solutions can be used to guide the mutation process, promoting a more exploitative search behavior.

## Procedure

### Data Structures

- Population: An array of candidate solutions, where each solution is a vector of real-valued parameters.
- Archive (optional): A separate array storing the best solutions found during the search.

### Parameters

- Population Size (NP): The number of candidate solutions in the population.
- Crossover Probability (CR): The probability of inheriting a dimension from the mutant vector during crossover.
- Scaling Factor (F): The weight applied to the difference vector during mutation.
- Maximum Generations (G_max): The maximum number of generations allowed before termination.

### Pseudocode

1. Initialize the population with NP randomly generated candidate solutions.
2. Evaluate the fitness of each candidate solution in the population.
3. While the termination criteria are not met (e.g., maximum generations):
   1. For each candidate solution (target vector) in the population:
      1. Select the best individual from the population as the base vector.
      2. Randomly select two distinct individuals from the population.
      3. Create a mutant vector by adding the scaled difference between the two selected individuals to the base vector.
      4. Perform binomial crossover between the mutant vector and the target vector to create an offspring vector.
      5. Evaluate the fitness of the offspring vector.
      6. If the offspring vector has a better fitness than the target vector, replace the target vector with the offspring vector in the population.
      7. (Optional) If using an external archive, update the archive with the best solutions found so far.
   2. Increment the generation counter.
4. Return the best solution found in the population or archive.

## Considerations

### Advantages

- Exploits the best solutions: By using the best individual as the base vector for mutation, DE/best/1/z focuses the search around promising regions of the search space.
- Balances exploration and exploitation: The use of an external archive allows for a more exploitative search while still maintaining diversity through the mutation and crossover operations.
- Simple and easy to implement: DE/best/1/z has a straightforward structure and requires minimal parameter tuning compared to other DE variants.

### Disadvantages

- Premature convergence: The emphasis on the best solutions may lead to premature convergence, especially in multimodal optimization problems with many local optima.
- Limited population diversity: As the search progresses, the population may lose diversity, reducing the algorithm's ability to escape local optima.
- Sensitivity to population size: The performance of DE/best/1/z can be sensitive to the choice of population size, requiring careful tuning for different problems.

## Heuristics

### Population Size (NP)

- As a general rule, set NP to 5-10 times the dimensionality of the problem.
- For complex multimodal problems, consider increasing NP to maintain population diversity.
- If the population size is too small, the algorithm may converge prematurely or struggle to find good solutions.

### Crossover Probability (CR)

- A common starting point is CR = 0.9, which allows for a high degree of information exchange between solutions.
- If the population diversity is low, consider reducing CR to introduce more exploration.
- For problems with strong interdependencies between variables, a higher CR can help preserve good solution structures.

### Scaling Factor (F)

- Typical values for F range from 0.5 to 1.0.
- Smaller values of F (around 0.5) promote exploitation, while larger values (around 1.0) encourage exploration.
- Adapt F during the search, starting with a larger value for exploration and gradually reducing it for exploitation.

### External Archive

- The size of the external archive can be set to a fraction of the population size (e.g., 25% of NP).
- Regularly update the archive with the best solutions found during the search.
- Consider strategies for maintaining diversity in the archive, such as clustering or crowding distance.
