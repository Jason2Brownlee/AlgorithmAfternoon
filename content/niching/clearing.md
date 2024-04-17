# Clearing

## Name

Clearing Genetic Algorithm (CGA), Clearing

## Taxonomy

The Clearing Genetic Algorithm is a variation of the canonical Genetic Algorithm, belonging to the field of Evolutionary Computation, which is a subfield of Computational Intelligence and Biologically Inspired Computation. It is closely related to other niching methods such as Crowding and Fitness Sharing.

- Computational Intelligence
  - Biologically Inspired Computation
    - Evolutionary Computation
      - Evolutionary Algorithms
        - Genetic Algorithms
          - Niching Methods
            - Clearing Genetic Algorithm

## Strategy

The Clearing Genetic Algorithm introduces a clearing procedure to the standard Genetic Algorithm to maintain population diversity and prevent premature convergence. This is achieved by dividing the population into subpopulations or niches based on the similarity of individuals.

### Niche Formation

Individuals are grouped into niches based on a similarity measure, typically defined by a distance metric in the search space. This allows the identification of distinct subpopulations that can explore different regions of the search space simultaneously.

### Clearing Procedure

Within each niche, the fitness of the best individual (dominant or winner) is preserved, while the fitness of all other individuals (subordinates) is reset to zero. This clearing procedure effectively eliminates competition within the niche, allowing the dominant individual to survive and propagate its genetic material.

### Niche Maintenance

The clearing procedure is applied at regular intervals (clearing rounds) to maintain the niches throughout the evolution process. This helps preserve diversity and prevents any single niche from taking over the entire population.

By incorporating the clearing procedure, the Clearing Genetic Algorithm promotes the formation and maintenance of stable niches, enabling the exploration of multiple optima in parallel. This makes it particularly suitable for multimodal optimization problems where multiple good solutions are desired.

## Procedure
### Data Structures
- Individual: A structure representing a candidate solution, which consists of:
  - Genotype: An array or string representing the genetic encoding of the solution.
  - Fitness: The fitness value of the individual.
- Population: An array of individuals.
- Clearing Radius: The distance threshold used to determine the niching or clearing of individuals.

### Parameters
- Population Size: The number of individuals in the population.
- Maximum Number of Generations: The maximum number of generations to run the algorithm.
- Crossover Probability: The probability of applying the crossover operator to create offspring.
- Mutation Probability: The probability of applying the mutation operator to modify an individual.
- Clearing Radius: The distance threshold for determining the niching or clearing of individuals.
- Niche Capacity: The maximum number of individuals allowed within a niche.

### Steps
1. Initialize the population
   1. For each individual in the population:
      1. Randomly initialize the genotype.
      2. Evaluate the fitness of the individual.
2. For each generation until the maximum number of generations is reached:
   1. Create a new population
      1. While the new population is not full:
         1. Select parent individuals using a selection method (e.g., tournament selection).
         2. Create offspring using genetic operators
            1. If a random number is less than the crossover probability:
               1. Apply the crossover operator to the selected parents to create two offspring.
            2. If a random number is less than the mutation probability:
               1. Apply the mutation operator to the offspring.
         3. Evaluate the fitness of the offspring.
         4. Add the offspring to the new population.
   2. Apply the clearing procedure
      1. Sort the individuals in the population based on their fitness values in descending order.
      2. For each individual in the sorted population:
         1. If the individual has not been cleared:
            1. Mark the individual as a niche winner.
            2. Clear the individuals within the clearing radius of the niche winner.
               1. For each individual within the clearing radius:
                  1. If the number of individuals in the niche exceeds the niche capacity:
                     1. Remove the individual from the population.
                  2. Else:
                     1. Mark the individual as cleared.
   3. Replace the old population with the new population.
3. Return the best individual found in the population.


## Considerations

Advantages:
- Maintains population diversity by preserving distinct niches throughout the evolution process
- Prevents premature convergence by allowing the exploration of multiple optima simultaneously
- Suitable for multimodal optimization problems where multiple good solutions are desired

Disadvantages:
- Increased computational complexity due to the additional clearing procedure
- Requires the definition of a suitable similarity measure and niche radius, which may be problem-dependent
- May struggle with high-dimensional search spaces where the formation of distinct niches becomes more challenging

## Heuristics

### Choosing the Niche Radius
- The niche radius should be selected based on the characteristics of the problem and the desired level of diversity
- A smaller niche radius results in more niches and higher diversity, while a larger radius leads to fewer niches and potentially faster convergence
- Experiment with different values to find a balance between diversity and convergence speed

### Setting the Clearing Interval
- The clearing interval determines how frequently the clearing procedure is applied
- A higher clearing interval allows more time for niches to evolve independently before being cleared
- A lower clearing interval provides more frequent updates to the niches but may slow down the overall convergence
- Adjust the clearing interval based on the problem complexity and the desired balance between diversity and convergence speed

### Population Size and Niche Capacity
- The population size should be sufficiently large to allow for the formation of multiple niches
- Consider the expected number of optima in the problem and ensure that the population size can accommodate the desired number of niches
- Monitor the number of individuals per niche (niche capacity) during the evolution process to ensure adequate representation of each niche

### Similarity Measure Selection
- Choose a similarity measure that effectively captures the relevant features of the problem domain
- Common similarity measures include Euclidean distance, Manhattan distance, and Hamming distance for binary representations
- Consider the nature of the problem and the encoding scheme when selecting an appropriate similarity measure

### Balancing Exploration and Exploitation
- Adjust the crossover and mutation probabilities to control the balance between exploration and exploitation
- Higher crossover probability promotes the exchange of genetic material between individuals, encouraging exploration
- Higher mutation probability introduces new genetic variations, allowing for further exploration of the search space
- Find a balance that maintains population diversity while allowing the exploitation of promising regions

