# Probabilistic Crowding

## Name

Probabilistic Crowding (PC)

## Taxonomy

Probabilistic Crowding is a technique in the field of Evolutionary Computation, which is a subfield of Computational Intelligence. It is closely related to other niching techniques such as Deterministic Crowding and Restricted Tournament Selection.

- Computational Intelligence
  - Evolutionary Computation
    - Evolutionary Algorithms
      - Genetic Algorithms
        - Niching Methods
          - Probabilistic Crowding

## Strategy

Probabilistic Crowding is a niching technique designed to maintain population diversity in genetic algorithms. It aims to prevent premature convergence and promote the formation of stable subpopulations around multiple optimal solutions.

The core idea behind Probabilistic Crowding is to pair individuals in the population based on their similarity and then apply selection pressure within each pair. This encourages competition between similar individuals, allowing different niches to evolve independently.

### Pairing Mechanism

In Probabilistic Crowding, each individual in the population is paired with another individual based on their genotypic or phenotypic similarity. The similarity measure can be based on techniques such as Hamming distance for binary representations or Euclidean distance for real-valued representations.

The pairing process is probabilistic, meaning that individuals with higher similarity have a higher probability of being paired together. This allows for some randomness in the pairing process while still promoting the formation of niches.

### Selection and Replacement

Once the individuals are paired, a selection mechanism is applied within each pair. Typically, a tournament selection is used, where the fitness values of the two individuals are compared, and the one with higher fitness is selected as the winner.

The winner of the tournament replaces the loser in the population. This replacement strategy ensures that the population size remains constant and that the fitter individuals survive and propagate their genetic material.

By applying selection pressure within each pair, Probabilistic Crowding encourages the formation of stable subpopulations around different optima. It allows individuals in different niches to evolve independently, preserving diversity and preventing premature convergence.

## Procedure

1. Initialize the population with a fixed size N.
2. While the termination condition is not met, repeat steps 3-7.
3. For each individual i in the population, do:
   1. Select another individual j from the population based on their similarity to i.
   2. Create an offspring o by applying genetic operators (crossover and mutation) to i and j.
   3. Evaluate the fitness of the offspring o.
   4. Conduct a tournament between i and o:
      1. If the fitness of o is better than the fitness of i, replace i with o in the population.
      2. Otherwise, discard o.
4. Repeat step 3 until all individuals in the population have been processed.
5. If the termination condition is met, stop the algorithm and return the final population.
6. Otherwise, go back to step 3 for the next generation.

### Data Structures

- Population: An array or list of individuals representing the current population.
- Individual: Represents a candidate solution in the search space. It can be encoded using various representations such as binary strings, real-valued vectors, or permutations, depending on the problem domain.
- Fitness Function: A function that evaluates the quality or fitness of an individual. It assigns a fitness value to each individual based on its performance on the given problem.

### Parameters

- Population Size (N): The number of individuals in the population. It determines the amount of genetic diversity and the exploration-exploitation trade-off.
- Similarity Measure: The metric used to calculate the similarity between individuals. Common choices include Hamming distance for binary representations and Euclidean distance for real-valued representations.
- Crossover Probability: The probability of applying the crossover operator to generate offspring. It controls the exploitation of good genetic material.
- Mutation Probability: The probability of applying the mutation operator to introduce random changes in the offspring. It maintains diversity and allows exploration of new regions in the search space.

## Considerations

### Advantages

- Maintains population diversity: Probabilistic Crowding promotes the formation of stable subpopulations around multiple optima, preventing premature convergence and allowing the exploration of different regions in the search space.
- Preserves niche information: By pairing individuals based on similarity and applying selection pressure within each pair, Probabilistic Crowding enables the preservation of niche-specific information and allows different niches to evolve independently.
- Enhances global optimization: Probabilistic Crowding helps in finding multiple optimal solutions in multimodal optimization problems. It is particularly useful when the goal is to identify a diverse set of high-quality solutions.

### Disadvantages

- Increased computational complexity: The pairing process in Probabilistic Crowding requires calculating similarities between individuals, which can be computationally expensive, especially for large population sizes and high-dimensional search spaces.
- Sensitivity to similarity measure: The performance of Probabilistic Crowding heavily relies on the choice of the similarity measure. Selecting an appropriate similarity measure that accurately captures the relevant features of the problem domain is crucial for effective niching.
- Parameter sensitivity: The effectiveness of Probabilistic Crowding can be sensitive to the values of its parameters, such as the population size and the similarity threshold. Proper tuning of these parameters is necessary to achieve optimal performance.

## Heuristics

### Population Size

- Set the population size large enough to maintain sufficient genetic diversity and allow for the formation of multiple niches.
- Consider the complexity of the problem and the desired number of optima when determining the population size.
- A larger population size can help in exploring a wider range of solutions but also increases the computational cost.

### Similarity Measure

- Choose a similarity measure that aligns with the problem representation and captures the relevant features of the search space.
- For binary representations, Hamming distance is commonly used, which measures the number of differing bits between two individuals.
- For real-valued representations, Euclidean distance is often employed, calculating the straight-line distance between two points in the search space.
- Consider normalizing the similarity measure to ensure fair comparisons between individuals.

### Genetic Operators

- Apply crossover and mutation operators that are suitable for the problem representation.
- For binary representations, bit-flip mutation and single-point or multi-point crossover are commonly used.
- For real-valued representations, Gaussian mutation and arithmetic crossover are popular choices.
- Adjust the probabilities of crossover and mutation based on the problem characteristics and desired exploration-exploitation balance.

### Termination Condition

- Define a suitable termination condition based on the problem requirements and available computational resources.
- Common termination conditions include reaching a maximum number of generations, achieving a desired fitness level, or observing convergence of the population.
- Consider incorporating a mechanism to detect stagnation and trigger termination if no significant improvement is observed over a certain number of generations.

### Niche Radius

- The niche radius determines the extent of each niche and influences the formation of subpopulations.
- Set the niche radius based on the problem domain and the desired level of diversity.
- A smaller niche radius leads to more focused and localized niches, while a larger radius allows for broader and more overlapping niches.
- Experiment with different niche radius values to find a balance between preserving diversity and allowing competition within niches.

