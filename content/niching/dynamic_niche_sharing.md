# Dynamic Niche Sharing

## Name

Dynamic Niche Sharing (DNS)

## Taxonomy

Dynamic Niche Sharing is a technique in the field of Evolutionary Computation, a subfield of Computational Intelligence. It is closely related to Fitness Sharing and Crowding techniques.

- Computational Intelligence
  - Evolutionary Computation
    - Genetic Algorithms
      - Niching Algorithms
        - Dynamic Niche Sharing

## Strategy

Dynamic Niche Sharing is a diversity preservation technique designed to maintain stable subpopulations (niches) within a genetic algorithm's population. It aims to prevent premature convergence and promote the exploration of multiple optima in multimodal optimization problems.

The core idea behind Dynamic Niche Sharing is to adjust the fitness of individuals based on their similarity to other individuals in the population. This is achieved by defining a sharing function that measures the distance between individuals in the search space. Individuals that are closer to each other (i.e., more similar) are considered to belong to the same niche and, therefore, share their fitness.

The sharing function typically involves a sharing radius parameter, which determines the size of each niche. Individuals within the sharing radius of each other have their fitness reduced proportionally to the number of individuals sharing that niche. This encourages the formation and maintenance of distinct niches, as individuals in less crowded regions of the search space will have higher relative fitness.

### Dynamic Adjustment of Sharing Radius

A key feature of Dynamic Niche Sharing is the dynamic adjustment of the sharing radius throughout the evolution process. The sharing radius is initially set to a large value, allowing the formation of broad niches. As the population evolves and begins to converge, the sharing radius is gradually reduced, leading to the formation of more localized niches around the discovered optima.

The dynamic adjustment of the sharing radius allows the algorithm to adapt to the structure of the fitness landscape and maintain a balance between exploration and exploitation. In the early stages, the large sharing radius promotes exploration by preventing the population from converging too quickly. As the search progresses, the decreasing sharing radius allows for a more fine-grained exploration of promising regions and the maintenance of stable niches around the discovered optima.

### Integration with Genetic Algorithm

Dynamic Niche Sharing is typically integrated into the selection process of a genetic algorithm. The adjusted fitness values, after applying the sharing function, are used to guide the selection of individuals for reproduction. This ensures that individuals from different niches have a fair chance of being selected, thus preserving diversity and preventing any single niche from dominating the population.

The dynamic sharing radius is updated at regular intervals, often tied to the generation count or a predefined schedule. The exact schedule and rate of reduction for the sharing radius can be adjusted based on the characteristics of the problem and the desired balance between exploration and exploitation.

## Procedure

1. Initialize the population:
   1. Generate a random initial population of individuals.
   2. Evaluate the fitness of each individual.

2. Set the initial sharing radius:
   - Determine the initial sharing radius based on the problem characteristics and desired niche size.

3. While the termination criteria are not met, repeat the following steps:

4. Apply the sharing function:
   1. For each individual in the population:
      1. Calculate the distance between the individual and every other individual in the population.
      2. Determine the number of individuals within the current sharing radius.
      3. Adjust the fitness of the individual based on the number of individuals sharing its niche.

5. Perform selection:
   - Select individuals for reproduction based on their adjusted fitness values.

6. Apply genetic operators:
   1. Perform crossover on the selected individuals to create offspring.
   2. Apply mutation to the offspring.

7. Evaluate the fitness of the new individuals.

8. Update the population:
   - Replace a portion of the population with the new individuals.

9. Update the sharing radius:
   - Adjust the sharing radius based on the predefined schedule or criteria.

10. Check the termination criteria:
    - If the termination criteria are met, stop the algorithm and return the best solution(s) found.
    - Otherwise, go back to step 4.

### Parameters

- Population Size: The number of individuals in the population.
- Sharing Radius: The initial value and reduction schedule for the sharing radius.
- Crossover Rate: The probability of applying crossover to selected individuals.
- Mutation Rate: The probability of applying mutation to the offspring.
- Replacement Strategy: The method for replacing individuals in the population with new offspring (e.g., elitism, steady-state).

## Considerations

### Advantages

- Maintains diversity: Dynamic Niche Sharing effectively preserves diversity within the population, preventing premature convergence to suboptimal solutions.
- Adapts to the fitness landscape: The dynamic adjustment of the sharing radius allows the algorithm to adapt to the structure of the fitness landscape, promoting exploration in the early stages and exploitation in later stages.
- Discovers multiple optima: By maintaining stable niches, Dynamic Niche Sharing is capable of discovering and preserving multiple optima in multimodal optimization problems.

### Disadvantages

- Sensitivity to parameters: The performance of Dynamic Niche Sharing is sensitive to the initial sharing radius and the reduction schedule. Inappropriate settings can lead to ineffective niche formation or insufficient diversity preservation.
- Increased computational complexity: The application of the sharing function requires calculating distances between individuals, which can be computationally expensive, especially for large populations or high-dimensional search spaces.
- Difficulty in setting the sharing radius: Determining an appropriate initial sharing radius and reduction schedule can be challenging, as it depends on the characteristics of the problem and may require problem-specific knowledge or experimentation.

## Heuristics

### Setting the Initial Sharing Radius

- Consider the size and dimensionality of the search space when setting the initial sharing radius.
- A larger initial sharing radius promotes broader exploration, while a smaller radius encourages more localized search.
- If prior knowledge about the problem is available, use it to guide the selection of the initial sharing radius.
- Experiment with different initial values and observe the impact on the algorithm's performance.

### Adjusting the Sharing Radius Reduction Schedule

- The sharing radius reduction schedule should balance exploration and exploitation over the course of the evolution.
- A gradual reduction allows for a smooth transition from global exploration to local exploitation.
- Consider the convergence behavior of the algorithm when deciding on the reduction rate.
- Faster reduction rates may lead to premature convergence, while slower rates may prolong the search unnecessarily.

### Handling High-Dimensional Search Spaces

- In high-dimensional search spaces, the effectiveness of Dynamic Niche Sharing may be limited due to the curse of dimensionality.
- Consider using dimensionality reduction techniques or problem-specific knowledge to focus the search on relevant dimensions.
- Adjust the sharing radius and reduction schedule to account for the increased sparsity of the search space in high dimensions.

### Balancing Population Size and Niche Size

- The population size should be large enough to maintain a sufficient number of niches and prevent loss of diversity.
- However, an excessively large population can slow down the convergence and increase computational overhead.
- Consider the trade-off between population size and niche size when configuring the algorithm.
- If the population size is limited, a smaller initial sharing radius may be necessary to ensure the formation of distinct niches.

### Combining with Other Diversity Preservation Techniques

- Dynamic Niche Sharing can be combined with other diversity preservation techniques, such as crowding or speciation.
- Integrating multiple techniques can further enhance the algorithm's ability to maintain diversity and explore the search space effectively.
- Experiment with different combinations and configurations to find the most suitable approach for the problem at hand.

