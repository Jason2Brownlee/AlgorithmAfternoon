# Elitist Genetic Algorithm

## Name
Elitist Genetic Algorithm (Elitist GA, Elitism GA)

## Taxonomy
The Elitist Genetic Algorithm is a variant of the Genetic Algorithm, which belongs to the field of Evolutionary Computation, a subfield of Computational Intelligence and Biologically Inspired Computation. It is closely related to other Genetic Algorithm variants such as the Steady-State Genetic Algorithm and the Generational Genetic Algorithm.

- Computational Intelligence
  - Biologically Inspired Computation
    - Evolutionary Computation
      - Evolutionary Algorithms
        - Genetic Algorithms
          - Elitist Genetic Algorithm

## Strategy
The Elitist Genetic Algorithm follows the standard Genetic Algorithm framework, with the addition of an elitism mechanism. This mechanism ensures that the best individuals from each generation are directly passed on to the next generation without being subjected to genetic operators like crossover and mutation.

The algorithm begins by initializing a population of candidate solutions, typically represented as binary strings or real-valued vectors. The fitness of each individual is evaluated using a predefined fitness function that measures the quality of the solution in the context of the given problem.

In each generation, a selection operator is applied to choose parent individuals for reproduction. Common selection methods include tournament selection, roulette wheel selection, and rank-based selection. The selected parents undergo crossover, where genetic information is exchanged between pairs of parents to create offspring. A mutation operator is then applied to introduce random changes in the offspring, promoting exploration of the search space.

The elitism mechanism is employed to preserve the best individuals from the current generation. These elite individuals are directly copied to the next generation, ensuring that the highest quality solutions are not lost during the evolutionary process. The remaining slots in the new population are filled with the offspring created through crossover and mutation.

This process of selection, crossover, mutation, and elitism is repeated for a predefined number of generations or until a satisfactory solution is found. The Elitist Genetic Algorithm maintains a balance between exploiting the best solutions found so far and exploring new regions of the search space, ultimately converging towards high-quality solutions.

## Procedure
### Data Structures
- Population: An array of individuals representing candidate solutions.
- Individual: A binary string or real-valued vector encoding a candidate solution.
- Fitness: A scalar value indicating the quality of an individual solution.

### Parameters
- Population Size: The number of individuals in the population.
- Crossover Rate: The probability of applying crossover to a pair of parents.
- Mutation Rate: The probability of applying mutation to an individual.
- Elite Size: The number of elite individuals to preserve in each generation.
- Max Generations: The maximum number of generations to run the algorithm.

### Pseudocode
1. Initialize the population with randomly generated individuals.
2. Evaluate the fitness of each individual in the population.
3. While the termination criterion is not met (e.g., max generations reached):
   1. Select parent individuals using a selection operator (e.g., tournament selection).
   2. Create offspring by applying crossover to the selected parents.
   3. Apply mutation to the offspring.
   4. Evaluate the fitness of the offspring.
   5. Select the elite individuals from the current population.
   6. Create the new population by combining the elite individuals and the offspring.
   7. Replace the current population with the new population.
4. Return the best individual found during the search.

## Considerations
### Advantages
- Elitism preserves the best solutions found so far, preventing the loss of high-quality individuals.
- Elitism can accelerate convergence by ensuring that the best solutions are always propagated to the next generation.
- The Elitist Genetic Algorithm often outperforms the standard Genetic Algorithm in terms of solution quality and convergence speed.

### Disadvantages
- The Elitist Genetic Algorithm may be more prone to premature convergence, especially if the elite size is too large.
- The increased selection pressure introduced by elitism can lead to reduced diversity in the population, potentially limiting exploration.
- The algorithm may require additional computational resources to maintain and update the elite individuals in each generation.

## Heuristics
### Population Size
- The population size should be large enough to maintain diversity and allow for effective exploration of the search space.
- A common heuristic is to set the population size between 50 and 200 individuals, depending on the problem complexity.
- If the population size is too small, the algorithm may struggle to find good solutions due to limited diversity.
- If the population size is too large, the algorithm may converge slowly and require more computational resources.

### Crossover Rate
- The crossover rate determines the probability of applying crossover to a pair of parents.
- A high crossover rate (e.g., 0.8 to 0.95) is typically recommended to promote the exchange of genetic information and the creation of new offspring.
- If the crossover rate is too low, the algorithm may rely heavily on mutation for generating new solutions, which can slow down convergence.

### Mutation Rate
- The mutation rate determines the probability of applying mutation to an individual.
- A low mutation rate (e.g., 0.01 to 0.1) is usually sufficient to introduce small variations and maintain diversity in the population.
- If the mutation rate is too high, the algorithm may become more random and struggle to converge towards good solutions.
- The mutation rate should be adjusted based on the problem size and the desired level of exploration.

### Elite Size
- The elite size determines the number of best individuals preserved in each generation.
- A small elite size (e.g., 1 to 5) is often sufficient to maintain the best solutions found so far.
- If the elite size is too large, the algorithm may converge prematurely and limit exploration of the search space.
- The elite size should be chosen to strike a balance between preserving high-quality solutions and allowing for diversity in the population.

### Termination Criteria
- The maximum number of generations is a common termination criterion, ensuring that the algorithm stops after a predefined number of iterations.
- Other termination criteria can include reaching a target fitness value, observing no improvement in the best fitness for a certain number of generations, or reaching a time limit.
- The choice of termination criteria depends on the problem requirements and available computational resources.
- It is important to set appropriate termination criteria to avoid unnecessary computations while still allowing the algorithm to converge towards good solutions.
