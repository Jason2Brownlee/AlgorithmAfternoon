---
title: DE/current-to-rand/1
---
# DE/current-to-rand/1

## Name

DE/current-to-rand/1, also known as: Differential Evolution "current-to-rand" mutation strategy and DE/c-to-r/1.

## Taxonomy

DE/current-to-rand/1 is a mutation strategy within the Differential Evolution (DE) algorithm, which belongs to the field of Evolutionary Computation, a subfield of Computational Intelligence. DE is closely related to other Evolutionary Algorithms such as Genetic Algorithms and Evolution Strategies.

- Computational Intelligence
  - Biologically Inspired Computation
    - Evolutionary Computation
      - Evolutionary Algorithms
        - Differential Evolution
          - DE Mutation Strategies
            - DE/current-to-rand/1

## Strategy

DE/current-to-rand/1 is a mutation strategy that generates new candidate solutions by combining the current individual with a scaled difference vector between two randomly selected individuals and a third randomly selected individual. This strategy introduces a degree of randomness into the mutation process, which can help maintain population diversity and improve the algorithm's ability to escape local optima.

The mutation process in DE/current-to-rand/1 can be described as follows:

1. For each individual in the current population, select three other individuals at random.
2. Calculate the difference vector between two of the randomly selected individuals.
3. Scale the difference vector by a mutation factor (F).
4. Add the scaled difference vector to the third randomly selected individual.
5. Combine the current individual with the result of step 4 using a weighting factor (K).
6. The resulting vector is the mutated individual.

This mutation strategy balances the exploitation of the current individual's information with the exploration of the search space through the introduction of random elements. The weighting factor (K) controls the influence of the current individual on the mutated individual, allowing for a trade-off between local and global search.

## Procedure

### Data Structures

- Population: A set of candidate solutions, each represented as a D-dimensional vector, where D is the number of decision variables in the optimization problem.
- Trial Vector: A new candidate solution generated by the mutation and crossover operations.

### Parameters

- Population Size (NP): The number of individuals in the population.
- Mutation Factor (F): A scaling factor applied to the difference vector during mutation, typically in the range [0, 2].
- Weighting Factor (K): A scalar value that determines the contribution of the current individual to the mutated individual, typically in the range [0, 1].
- Crossover Probability (CR): The probability of performing crossover between the mutated individual and the current individual, typically in the range [0, 1].

### Pseudocode

1. Initialize the population with NP individuals randomly distributed in the search space.
2. While the termination criterion is not met, do:
   1. For each individual xi in the population, do:
      1. Select three random individuals xr1, xr2, and xr3 from the population, where i ≠ r1 ≠ r2 ≠ r3.
      2. Calculate the mutated individual vi using the DE/current-to-rand/1 mutation strategy:
         1. Calculate the difference vector: dv = xr2 - xr3
         2. Scale the difference vector: sdv = F * dv
         3. Add the scaled difference vector to xr1: nv = xr1 + sdv
         4. Combine the current individual with nv: vi = K * xi + (1 - K) * nv
      3. Perform crossover between xi and vi to generate a trial vector ui.
      4. Evaluate the fitness of the trial vector ui.
      5. If ui has a better fitness than xi, replace xi with ui in the population.
   2. Check if the termination criterion is met.
3. Return the best individual found in the population as the solution.

## Considerations

### Advantages

- Introduces a degree of randomness in the mutation process, which can help maintain population diversity and avoid premature convergence.
- Balances exploitation of the current individual's information with exploration of the search space.
- Allows for a trade-off between local and global search through the weighting factor (K).

### Disadvantages

- The performance of the algorithm depends on the appropriate setting of the control parameters (F, K, and CR), which may require problem-specific tuning.
- The randomness introduced by this mutation strategy may slow down convergence compared to more exploitative strategies.
- The effectiveness of the algorithm may be reduced in problems with highly correlated decision variables.

## Heuristics

### Mutation Factor (F)

- A small value of F (e.g., 0.1 to 0.5) favors exploitation, while a larger value (e.g., 0.5 to 1.0) favors exploration.
- If the population diversity is low, increasing F can help maintain diversity and avoid premature convergence.
- If the algorithm is converging too slowly, reducing F can help speed up convergence.

### Weighting Factor (K)

- A small value of K (e.g., 0.1 to 0.3) gives more weight to the randomly generated individual, favoring exploration.
- A larger value of K (e.g., 0.7 to 0.9) gives more weight to the current individual, favoring exploitation.
- If the algorithm is converging too quickly to a suboptimal solution, reducing K can help maintain population diversity.
- If the algorithm is converging too slowly, increasing K can help speed up convergence.

### Crossover Probability (CR)

- A small value of CR (e.g., 0.1 to 0.3) results in fewer components of the trial vector being inherited from the mutated individual, favoring exploitation.
- A larger value of CR (e.g., 0.7 to 0.9) results in more components of the trial vector being inherited from the mutated individual, favoring exploration.
- If the algorithm is converging too quickly to a suboptimal solution, increasing CR can help maintain population diversity.
- If the algorithm is converging too slowly, decreasing CR can help speed up convergence.

### Population Size (NP)

- A smaller population size (e.g., 20 to 50) can lead to faster convergence but may increase the risk of premature convergence.
- A larger population size (e.g., 100 to 500) can help maintain population diversity and improve the algorithm's ability to explore the search space but may slow down convergence.
- The optimal population size depends on the problem complexity and the available computational resources.
- As a general rule, the population size should be at least 10 times the dimensionality of the problem.

