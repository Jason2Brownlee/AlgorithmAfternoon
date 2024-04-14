# Sequential Niching

## Name

Sequential Niching, Sequential Niche Method, SNM

## Taxonomy

Sequential Niching is a technique in the field of Evolutionary Computation, which is a subfield of Computational Intelligence. It is closely related to niching methods such as Fitness Sharing and Crowding.

- Artificial Intelligence
  - Computational Intelligence
    - Evolutionary Computation
      - Evolutionary Algorithms
        - Niching Methods
          - Sequential Niching

## Strategy

Sequential Niching is a method for maintaining population diversity and promoting the exploration of multiple optima in evolutionary algorithms. It operates by iteratively applying a standard evolutionary algorithm to a population, locating a single optimum, and then "removing" that optimum from the search space to allow the algorithm to locate additional optima.

The core idea behind Sequential Niching is to modify the fitness landscape after each successful run of the evolutionary algorithm. This modification is performed in such a way that the previously located optimum is no longer attractive to the search process, effectively forcing the algorithm to explore other areas of the search space.

### Fitness Modification

The fitness modification step is crucial to the functioning of Sequential Niching. After an optimum is located, the fitness function is modified in the region surrounding that optimum. This modification typically involves reducing the fitness values in that region, making it less attractive to future search iterations.

Various techniques can be used for fitness modification, such as fitness sharing, where the fitness of individuals in the population is reduced based on their similarity to the located optimum. Another approach is to directly modify the fitness function itself, adding a "penalty term" centered around the located optimum.

### Iteration and Termination

The Sequential Niching process iterates between running the evolutionary algorithm and modifying the fitness landscape. Each iteration is expected to locate a single optimum, which is then removed from consideration in subsequent iterations.

The process terminates when a predefined number of optima have been located, or when the evolutionary algorithm fails to locate a new optimum within a certain number of iterations. At this point, the algorithm returns the set of optima that were located during the search process.

## Procedure

1. Initialize the set of located optima to an empty set.
2. While the termination criteria are not met:
   1. Initialize a population of individuals.
   2. Run a standard evolutionary algorithm on the population:
      1. Evaluate the fitness of each individual.
      2. Select parents for reproduction.
      3. Apply genetic operators (crossover and mutation) to create offspring.
      4. Replace the population with the offspring.
      5. If the stopping criteria for the evolutionary algorithm are met, continue to the next step. Otherwise, go back to step 2.2.1.
   3. Identify the best individual in the final population as a located optimum.
   4. If the located optimum is sufficiently different from the previously located optima, add it to the set of located optima. Otherwise, discard it.
   5. Modify the fitness landscape to "remove" the located optimum:
      1. Define a region around the located optimum.
      2. Reduce the fitness values of individuals within that region, or modify the fitness function to add a penalty term in that region.
3. Return the set of located optima.

### Data Structures

- Population: An array of individuals, where each individual represents a potential solution to the problem.
- Located Optima: An array storing the optima that have been located during the search process.

### Parameters

- Population Size: The number of individuals in the population.
- Evolutionary Algorithm Parameters: The parameters specific to the evolutionary algorithm being used, such as the selection method, crossover rate, and mutation rate.
- Fitness Modification Parameters: The parameters controlling the fitness modification process, such as the size of the region around each located optimum and the severity of the fitness reduction.
- Termination Criteria: The conditions under which the Sequential Niching process should terminate, such as the maximum number of optima to locate or the maximum number of iterations without locating a new optimum.

## Considerations

### Advantages

- Effective at locating multiple optima: Sequential Niching is designed to locate multiple optima in the search space, making it suitable for multimodal optimization problems.
- Maintains population diversity: By iteratively modifying the fitness landscape, Sequential Niching encourages the population to explore different regions of the search space, thus maintaining diversity.
- Customizable fitness modification: The fitness modification step can be adapted to suit the specific problem and the characteristics of the fitness landscape.

### Disadvantages

- Increased computational complexity: The iterative nature of Sequential Niching and the need to modify the fitness landscape after each iteration can increase the computational complexity compared to standard evolutionary algorithms.
- Dependence on fitness modification parameters: The performance of Sequential Niching can be sensitive to the choice of fitness modification parameters, such as the size of the region around each optimum and the severity of the fitness reduction.
- Limited by the underlying evolutionary algorithm: The effectiveness of Sequential Niching is ultimately dependent on the performance of the underlying evolutionary algorithm. If the evolutionary algorithm struggles to locate optima in the original fitness landscape, Sequential Niching may also struggle.

## Heuristics

### Population Size

- Use a population size that is large enough to maintain diversity and explore the search space effectively, but not so large that computational efficiency is compromised.
- Consider increasing the population size for more complex problems or higher-dimensional search spaces.

### Fitness Modification

- Choose a fitness modification method that is appropriate for the problem and the characteristics of the fitness landscape. Fitness sharing and penalty terms are common choices.
- Adjust the size of the region around each located optimum based on the expected distance between optima in the search space. A larger region may be needed for widely separated optima, while a smaller region may be sufficient for closely spaced optima.
- Tune the severity of the fitness reduction to balance the exploration of new optima with the exploitation of already located optima. A too-severe reduction may overly discourage the algorithm from exploring nearby regions, while a too-mild reduction may not effectively encourage the exploration of new optima.

### Termination Criteria

- Set a maximum number of optima to locate based on the known or expected number of optima in the problem.
- Use a maximum number of iterations without locating a new optimum to prevent the algorithm from wasting computational resources when all optima have likely been located.
- Consider using a relative improvement threshold as an additional termination criterion, stopping the algorithm when the quality of newly located optima falls below a certain threshold compared to previously located optima.

### Integration with Other Techniques

- Sequential Niching can be combined with various evolutionary algorithms, such as Genetic Algorithms, Evolution Strategies, and Differential Evolution. Choose an evolutionary algorithm that is well-suited to the specific problem.
- Consider integrating local search techniques, such as hill climbing or simulated annealing, to refine the located optima and improve the overall solution quality.
- Experiment with different population initialization strategies, such as latin hypercube sampling or opposition-based learning, to improve the initial coverage of the search space and the diversity of the initial population.

