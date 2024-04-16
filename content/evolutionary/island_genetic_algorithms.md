# Island Genetic Algorithms

## Name
Island Genetic Algorithms (IGA), Island Model Genetic Algorithms (IMGA), Island Parallel Genetic Algorithms (IPGA), Distributed Genetic Algorithms (DGA)

## Taxonomy
Island Genetic Algorithms are a variant of Genetic Algorithms that incorporate a spatial population structure, inspired by the evolutionary processes observed in geographically isolated populations. They are closely related to other spatially structured evolutionary algorithms such as Cellular Genetic Algorithms and Diffusion Genetic Algorithms.

- Computational Intelligence
  - Biologically Inspired Computation
    - Evolutionary Computation
      - Evolutionary Algorithms
        - Genetic Algorithms
          - Island Genetic Algorithms

## Strategy

### Population Structure
In Island Genetic Algorithms, the population is divided into multiple subpopulations, each referred to as an "island." These islands evolve independently for a certain number of generations, with occasional migration of individuals between islands. This structure allows for greater diversity preservation and reduces the risk of premature convergence.

### Migration
Periodically, a subset of individuals from each island is selected to migrate to other islands. The migration topology, which defines the connectivity between islands, can vary from a simple ring topology to more complex structures like a fully connected graph or a custom-defined network. The migration rate and frequency are key parameters that influence the algorithm's performance.

### Island Evolution
Each island operates as a separate Genetic Algorithm, applying selection, crossover, and mutation operators to its local population. The evolutionary process within each island can be fine-tuned independently, allowing for heterogeneous search strategies across the islands. This enables the exploration of different regions of the search space and the preservation of diverse solution characteristics.

### Convergence and Termination
The Island Genetic Algorithm terminates when a predefined criterion is met, such as reaching a maximum number of generations or finding a solution of sufficient quality. Upon termination, the best solutions from each island are typically compared, and the overall best solution is reported as the final result.

## Procedure

### Data Structures
- Population: A collection of individuals representing potential solutions to the problem.
- Island: A subpopulation of individuals that evolves independently.
- Migration Policy: Defines the topology, rate, and frequency of migration between islands.

### Parameters
- Number of Islands: The number of subpopulations in the algorithm.
- Island Size: The number of individuals within each island.
- Migration Topology: The connectivity pattern between islands (e.g., ring, fully connected, custom).
- Migration Rate: The proportion of individuals that migrate from each island during a migration event.
- Migration Frequency: The number of generations between migration events.
- Selection Method: The strategy used to select individuals for reproduction (e.g., tournament, roulette wheel).
- Crossover Operator: The operator used to combine genetic information from parents to create offspring.
- Mutation Operator: The operator used to introduce random changes in the genetic information of individuals.
- Termination Criteria: The conditions that determine when the algorithm should stop (e.g., maximum generations, solution quality threshold).

### Algorithm Steps
1. Initialize the population:
   1. Create a population of individuals.
   2. Divide the population into a specified number of islands.
2. Evaluate the fitness of each individual in the population.
3. For each island, perform the following steps until the termination criteria are met:
   1. Select parents for reproduction based on the selection method.
   2. Apply the crossover operator to the selected parents to create offspring.
   3. Apply the mutation operator to the offspring with a specified probability.
   4. Evaluate the fitness of the offspring.
   5. Replace the current island population with the offspring based on a replacement strategy (e.g., elitism, generational).
   6. If the migration frequency is reached, perform migration:
      1. Select a subset of individuals from the island based on the migration rate.
      2. Send the selected individuals to the connected islands according to the migration topology.
      3. Receive migrated individuals from connected islands and integrate them into the island population.
4. Compare the best solutions from each island and report the overall best solution.

## Considerations

### Advantages
- Preserved Diversity: The island structure helps maintain genetic diversity by allowing subpopulations to evolve independently, reducing the risk of premature convergence.
- Parallelization: Island Genetic Algorithms are inherently parallel, as each island can be processed independently on separate computing resources, leading to improved efficiency.
- Robustness: The distributed nature of Island Genetic Algorithms makes them more resilient to local optima traps and allows for the exploration of different regions of the search space.

### Disadvantages
- Parameter Sensitivity: The performance of Island Genetic Algorithms heavily depends on the proper configuration of migration parameters, such as topology, rate, and frequency, which can be challenging to tune.
- Communication Overhead: The migration of individuals between islands introduces communication overhead, which can impact the overall efficiency of the algorithm, especially when dealing with large-scale problems or limited communication bandwidth.
- Synchronization: Depending on the implementation, Island Genetic Algorithms may require synchronization points between islands, which can lead to idle time if the islands evolve at different speeds.

## Heuristics

### Island Configuration
- Start with a moderate number of islands (e.g., 5-10) and adjust based on the problem complexity and available computational resources.
- Ensure that each island has a sufficient population size to maintain diversity and avoid premature convergence within the island.
- Experiment with different island sizes and population sizes to find a balance between exploration and exploitation.

### Migration Topology
- Use a simple migration topology (e.g., ring) for initial experiments and gradually explore more complex topologies if needed.
- Consider the problem structure and the desired level of interaction between islands when selecting the migration topology.
- Customize the migration topology based on domain knowledge or problem-specific requirements.

### Migration Rate and Frequency
- Start with a low migration rate (e.g., 5-10% of the island population) to allow sufficient time for each island to evolve independently.
- Adjust the migration rate based on the problem complexity and the desired level of diversity preservation.
- Set the migration frequency to allow several generations of evolution within each island before migration occurs (e.g., every 10-20 generations).
- Experiment with different migration rates and frequencies to find a balance between diversity preservation and convergence speed.

### Operator Configuration
- Use standard Genetic Algorithm operators (e.g., tournament selection, single-point crossover, bit-flip mutation) as a starting point.
- Adjust the operator parameters (e.g., tournament size, crossover probability, mutation probability) based on the problem characteristics and desired search behavior.
- Consider using adaptive or self-adjusting operator parameters to dynamically control the exploration-exploitation balance.

### Termination Criteria
- Define a maximum number of generations based on the problem complexity and available computational resources.
- Incorporate a solution quality threshold as an additional termination criterion to stop the algorithm when a satisfactory solution is found.
- Monitor the progress of the best solutions across islands and consider terminating the algorithm if no significant improvement is observed over a certain number of generations.
