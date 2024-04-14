# Novelty Search With Local Competition

## Name

Novelty Search with Local Competition (NS-LC)

## Taxonomy

Novelty Search with Local Competition is an extension of the Novelty Search algorithm that incorporates local competition to balance exploration and exploitation in evolutionary algorithms. It is a technique within the fields of Evolutionary Computation, Stochastic Optimization, and Biologically Inspired Computation.

- Computational Intelligence
  - Biologically Inspired Computation
    - Evolutionary Computation
      - Evolutionary Algorithms
        - Genetic Algorithms
          - Novelty Search
            - Novelty Search with Local Competition

## Strategy

Novelty Search with Local Competition builds upon the core principles of Novelty Search, which promotes exploration by rewarding individuals that exhibit novel behaviors rather than those that directly optimize a fitness function. In Novelty Search, the novelty of an individual is determined by comparing its behavior to an archive of previously encountered behaviors, with more novel individuals receiving higher priority for reproduction.

NS-LC introduces the concept of local competition alongside novelty by considering both the novelty and the local quality of individuals within their behavioral neighborhood. The local quality of an individual is determined by its performance relative to nearby individuals in the behavior space. By incorporating this local competition, NS-LC strikes a balance between exploring novel regions of the behavior space and exploiting high-quality solutions within those regions.

The algorithm maintains an archive of novel individuals and their behaviors throughout the evolutionary process. In each generation, individuals are evaluated based on their novelty and local quality scores. The novelty score is calculated by measuring the behavioral distance between an individual and its nearest neighbors in the archive, while the local quality score is determined by comparing the fitness of an individual to its nearest neighbors in the current population.

Selection and reproduction in NS-LC are based on a combination of novelty and local quality scores, with higher-scoring individuals having a greater chance of being selected as parents for the next generation. This selection mechanism ensures that the population explores novel regions of the behavior space while also promoting the refinement of high-quality solutions within those regions.

## Procedure

### Data Structures

- Population: A collection of individuals representing potential solutions to the problem.
- Archive: A collection of novel individuals and their behaviors encountered throughout the evolutionary process.
- Behavior Characterization: A method for encoding the behavior of an individual into a compact representation (e.g., a vector of real numbers).
- Behavioral Distance Metric: A function that measures the dissimilarity between two behavior characterizations.

### Parameters

- Population Size: The number of individuals in each generation of the evolutionary algorithm.
- Novelty Threshold: The minimum behavioral distance required for an individual to be considered novel and added to the archive.
- Nearest Neighbors (k): The number of nearest neighbors considered when calculating novelty and local quality scores.
- Reproduction Operators: The genetic operators used for creating new individuals, such as mutation and crossover.

### Pseudocode

1. Initialize the population with random individuals.
2. Initialize an empty archive.
3. While the termination criterion is not met:
   1. Evaluate each individual in the population:
      1. Calculate the behavior characterization of the individual.
      2. Calculate the novelty score of the individual:
         1. Find the k-nearest neighbors of the individual in the archive based on the behavioral distance metric.
         2. Calculate the average behavioral distance between the individual and its k-nearest neighbors.
      3. Calculate the local quality score of the individual:
         1. Find the k-nearest neighbors of the individual in the current population based on the behavioral distance metric.
         2. Calculate the relative fitness of the individual compared to its k-nearest neighbors.
   2. Update the archive:
      1. For each individual in the population:
         1. If the novelty score of the individual exceeds the novelty threshold, add it to the archive.
   3. Select parents for reproduction based on a combination of novelty and local quality scores.
   4. Create the next generation by applying reproduction operators to the selected parents.
4. Return the best individual found during the evolutionary process.

## Considerations

### Advantages

- Promotes exploration of novel solutions, avoiding premature convergence to suboptimal regions of the search space.
- Balances exploration and exploitation by considering both novelty and local quality of individuals.
- Enables the discovery of diverse and high-quality solutions in complex search spaces.

### Disadvantages

- Requires the definition of an appropriate behavior characterization and distance metric, which can be problem-specific and challenging to design.
- The archive size may grow large over time, increasing computational overhead for calculating novelty scores.
- The performance of the algorithm is sensitive to the choice of parameters, such as the novelty threshold and the number of nearest neighbors considered.

## Heuristics

### Behavior Characterization

- Choose a behavior characterization that captures the relevant aspects of an individual's behavior in the problem domain.
- The behavior characterization should be compact and computationally efficient to calculate.
- Consider using domain-specific knowledge or automated feature extraction techniques to design informative behavior characterizations.

### Distance Metric

- Select a distance metric that accurately measures the dissimilarity between behavior characterizations.
- Common choices include Euclidean distance, Manhattan distance, or cosine distance, depending on the nature of the behavior space.
- Experiment with different distance metrics and assess their impact on the algorithm's performance.

### Novelty Threshold

- Set the novelty threshold to strike a balance between promoting exploration and managing the size of the archive.
- A high novelty threshold may lead to a smaller archive and less exploration, while a low threshold may result in a larger archive and increased computational overhead.
- Adapt the novelty threshold dynamically based on the progress of the evolutionary process or the characteristics of the problem domain.

### Nearest Neighbors (k)

- Choose a value of k that provides a reasonable estimate of the local neighborhood in the behavior space.
- A small value of k may lead to noisy novelty and local quality estimates, while a large value may overgeneralize the neighborhood and reduce the effectiveness of local competition.
- Experiment with different values of k and assess their impact on the algorithm's performance.

### Reproduction Operators

- Select reproduction operators that are suitable for the problem domain and the representation of individuals.
- Common choices include mutation operators that introduce small perturbations to individuals and crossover operators that combine genetic material from parents.
- Adapt the reproduction operators to maintain diversity and promote the generation of novel and high-quality offspring.

