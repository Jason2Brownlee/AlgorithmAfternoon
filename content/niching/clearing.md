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

1. Initialize the population
   1.1. Create a population of N individuals with randomly generated genotypes
   1.2. Evaluate the fitness of each individual in the population

2. While termination criteria not met, repeat:
   2.1. Apply the clearing procedure
       2.1.1. Divide the population into niches based on a similarity measure (e.g., Euclidean distance)
       2.1.2. Within each niche:
           2.1.2.1. Identify the individual with the highest fitness (dominant or winner)
           2.1.2.2. Reset the fitness of all other individuals (subordinates) to zero
   2.2. Select parents for reproduction using a selection method (e.g., tournament selection)
   2.3. Create offspring by applying genetic operators
       2.3.1. Apply crossover operator to selected parents to create offspring
       2.3.2. Apply mutation operator to offspring with a given mutation probability
   2.4. Evaluate the fitness of the offspring
   2.5. Replace the population with the offspring using a replacement strategy (e.g., elitist replacement)

3. Return the best solution found

### Data Structures:
- Population: An array or list of individuals representing potential solutions
- Individual: Represents a single solution, typically encoded as a string of bits, real numbers, or other data types
- Niche: A subset of individuals in the population that are similar based on a predefined similarity measure

### Parameters:
- Population Size: The number of individuals in the population
- Niche Radius: The maximum distance between individuals to be considered part of the same niche
- Clearing Interval: The number of generations between each application of the clearing procedure
- Crossover Probability: The probability of applying the crossover operator to selected parents
- Mutation Probability: The probability of applying the mutation operator to offspring

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

