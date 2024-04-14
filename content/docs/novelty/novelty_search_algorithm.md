# Novelty Search Algorithm

## Name

Novelty Search, NS

## Taxonomy

Novelty Search is a search technique in the field of Evolutionary Computation, which itself is a subfield of Computational Intelligence and Biologically Inspired Computation. It is closely related to other evolutionary algorithms such as Genetic Algorithms and Neuroevolution.

- Computational Intelligence
  - Biologically Inspired Computation
    - Evolutionary Computation
      - Evolutionary Algorithms
        - Genetic Algorithms
        - Neuroevolution
      - Novelty Search

## Strategy

Novelty Search is a search strategy that aims to find novel solutions rather than solutions that directly optimize a predefined fitness function. It operates by maintaining an archive of previously encountered behaviors and guiding the search towards behaviors that are different from those already in the archive.

### Behavior Characterization

In Novelty Search, each individual in the population is characterized by its behavior, which is typically a low-dimensional representation of what the individual does in the problem domain. This behavior characterization is used to compare individuals and determine their novelty.

### Novelty Metric

The novelty of an individual is determined by measuring its behavioral distance to its nearest neighbors in the behavior space. This distance is calculated using a novelty metric, which quantifies the dissimilarity between two behaviors. Common novelty metrics include Euclidean distance and Hamming distance.

### Archive Management

Novelty Search maintains an archive of novel behaviors encountered during the search. When a new individual is evaluated, its behavior is compared to those in the archive. If the individual's behavior is sufficiently different (i.e., novel), it is added to the archive. The archive may have a fixed size, in which case less novel behaviors are removed when new ones are added.

### Selection and Reproduction

In each generation of Novelty Search, a subset of individuals is selected for reproduction based on their novelty scores. Individuals with higher novelty scores, i.e., those with behaviors that are more different from the ones in the archive, have a higher chance of being selected. Selected individuals are then used to create the next generation through genetic operators like crossover and mutation.

## Procedure

1. Initialize population
2. Initialize empty archive
3. While termination condition not met:
   1. Evaluate each individual in the population:
      1. Characterize individual's behavior
      2. Calculate novelty score:
         1. Compute distance to k-nearest neighbors in archive
         2. Assign novelty score based on average distance
   2. Add individuals with sufficiently novel behaviors to archive
   3. If archive size exceeds maximum:
      1. Remove least novel individuals from archive
   4. Select parents based on novelty scores
   5. Create next generation through crossover and mutation
4. Return final population and archive

### Data Structures

- Population: A collection of individuals representing potential solutions
- Archive: A collection of novel behaviors encountered during the search
- Behavior representation: A low-dimensional characterization of an individual's behavior
- Novelty metric: A measure of dissimilarity between two behaviors

### Parameters

- Population size: Number of individuals in the population
- Archive size: Maximum number of behaviors to maintain in the archive
- Novelty threshold: Minimum novelty score required for an individual to be added to the archive
- Nearest neighbors (k): Number of nearest neighbors to consider when calculating novelty scores
- Crossover rate: Probability of applying crossover during reproduction
- Mutation rate: Probability of applying mutation during reproduction

## Considerations

### Advantages

- Promotes exploration of the search space
- Discovers diverse and unexpected solutions
- Avoids premature convergence to local optima
- Suitable for problems with deceptive or hard-to-define fitness functions

### Disadvantages

- Computationally expensive, especially for large behavior spaces
- Requires careful design of behavior characterization and novelty metric
- Does not globally optimize, meaning solutions may not have the globally optimal fitness if mapping to a fitness metric after the search

## Heuristics

### Behavior Characterization

- Choose a behavior characterization that captures relevant aspects of the problem domain
- Avoid overly complex or high-dimensional behavior representations
- Ensure the behavior characterization is computationally efficient to evaluate

### Novelty Metric

- Select a novelty metric that is appropriate for the behavior representation
- Consider normalizing behavior dimensions to ensure equal contribution to novelty scores
- Experiment with different distance metrics (e.g., Euclidean, Manhattan, Hamming) to find the most suitable one

### Archive Management

- Set the archive size based on the available computational resources and desired diversity
- Adjust the novelty threshold to control the trade-off between exploration and exploitation
- Consider periodically pruning the archive to remove obsolete or less informative behaviors

### Population and Reproduction

- Adjust population size based on problem complexity and available computational resources
- Set crossover and mutation rates to maintain a balance between exploration and exploitation
- Experiment with different parent selection strategies (e.g., tournament selection, fitness proportionate selection) to find the most effective one for the problem at hand

### Integration with Other Techniques

- Consider combining Novelty Search with other evolutionary algorithms or optimization techniques
- Use Novelty Search as a diversity maintenance mechanism within a larger optimization framework
- Incorporate domain-specific knowledge or heuristics to guide the search towards promising regions of the behavior space