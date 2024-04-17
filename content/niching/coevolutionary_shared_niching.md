# Coevolutionary Shared Niching

## Name
Coevolutionary Shared Niching (CSN)

## Taxonomy
Coevolutionary Shared Niching is a technique in the field of Evolutionary Computation, which is a subfield of Computational Intelligence. It is closely related to other coevolutionary algorithms such as Cooperative Coevolution and Competitive Coevolution.

- Computational Intelligence
  - Evolutionary Computation
    - Evolutionary Algorithms
      - Genetic Algorithms
      - Coevolutionary Algorithms
        - Cooperative Coevolution
        - Competitive Coevolution
        - Coevolutionary Shared Niching

## Strategy
Coevolutionary Shared Niching is a technique that combines the principles of coevolution and niching to maintain population diversity and prevent premature convergence in evolutionary algorithms. The algorithm maintains multiple subpopulations, each focusing on a specific subproblem or niche of the search space.

### Subpopulations and Niches
In CSN, the population is divided into several subpopulations, each representing a different niche or subproblem. These subpopulations evolve independently, allowing them to specialize in their respective niches. This division helps maintain diversity and prevents any single subpopulation from dominating the search process.

### Coevolution and Interaction
The subpopulations in CSN coevolve, meaning they influence each other's evolution through their interactions. Individuals from different subpopulations are evaluated based on their performance against individuals from other subpopulations. This interaction creates a dynamic fitness landscape, where the fitness of an individual depends on its ability to solve its specific subproblem and its performance against other subpopulations.

### Shared Fitness and Collaboration
CSN introduces the concept of shared fitness, where the fitness of an individual is determined not only by its own performance but also by the performance of individuals from other subpopulations that share the same niche. This encourages collaboration between individuals within the same niche, as their success is tied to the success of their niche as a whole.

### Niche Radius and Crowding
To maintain diversity within each niche, CSN employs a crowding mechanism based on the niche radius. The niche radius determines the distance threshold within which individuals are considered to be in the same niche. When the number of individuals within a niche exceeds a certain limit, the crowding mechanism removes the least fit individuals to prevent overcrowding and maintain diversity.

## Procedure
### Data Structures
- Individual: A structure representing a candidate solution, which consists of:
  - Genotype: An array or string representing the genetic encoding of the solution.
  - Fitness: The fitness value of the individual.
  - Species: The species to which the individual belongs.
- Population: An array of individuals.
- Species: A set of individuals that share similar characteristics or belong to the same niche.
- Shared Fitness: The fitness value of an individual after applying the shared niching mechanism.

### Parameters
- Population Size: The number of individuals in the population.
- Maximum Number of Generations: The maximum number of generations to run the algorithm.
- Crossover Probability: The probability of applying the crossover operator to create offspring.
- Mutation Probability: The probability of applying the mutation operator to modify an individual.
- Niche Radius: The distance threshold for determining the sharing of fitness among individuals.
- Sharing Function: A function that determines the degree of sharing between individuals based on their distance.

### Steps
1. Initialize the population
   1. For each individual in the population:
      1. Randomly initialize the genotype.
      2. Evaluate the fitness of the individual.
      3. Assign the individual to a species based on its characteristics.
2. For each generation until the maximum number of generations is reached:
   1. Apply the shared niching mechanism
      1. For each species:
         1. Calculate the shared fitness of individuals within the species
            1. For each individual in the species:
               1. Calculate the niche count
                  1. For each other individual in the population:
                     1. Calculate the distance between the individuals.
                     2. If the distance is within the niche radius:
                        1. Increment the niche count of the individual.
               2. Calculate the shared fitness of the individual
                  1. Divide the individual's fitness by its niche count.
   2. Create a new population
      1. While the new population is not full:
         1. Select parent individuals using a selection method based on shared fitness (e.g., tournament selection).
         2. Create offspring using genetic operators
            1. If a random number is less than the crossover probability:
               1. Apply the crossover operator to the selected parents to create two offspring.
            2. If a random number is less than the mutation probability:
               1. Apply the mutation operator to the offspring.
         3. Evaluate the fitness of the offspring.
         4. Assign the offspring to a species based on its characteristics.
         5. Add the offspring to the new population.
   3. Replace the old population with the new population.
   4. Perform coevolutionary operations
      1. Migrate individuals between species
         1. Select a subset of individuals from each species.
         2. Move the selected individuals to different species based on their characteristics.
      2. Adapt species based on their performance
         1. Evaluate the overall fitness of each species.
         2. Adjust the species parameters (e.g., niche radius) based on their performance.
         3. Create new species or merge existing species if necessary.
3. Return the best individual found in the population.


## Considerations
### Advantages
- Maintains population diversity by preserving multiple niches
- Prevents premature convergence by avoiding dominance of a single subpopulation
- Promotes collaboration and specialization through coevolution and shared fitness
- Allows for efficient exploration of complex and multimodal search spaces

### Disadvantages
- Increased computational complexity due to the evaluation of individuals against multiple subpopulations
- Requires careful tuning of parameters, such as the number of subpopulations and the niche radius
- May struggle with problems that have a large number of niches or overlapping subproblems
- The performance heavily depends on the appropriate definition of niches and the effectiveness of the crowding mechanism

## Heuristics
### Determining the Number of Subpopulations
- Consider the number of distinct subproblems or niches in the problem domain
- Experiment with different values and observe the impact on population diversity and convergence
- A larger number of subpopulations can lead to better diversity but may increase computational overhead

### Setting the Niche Radius
- The niche radius should be large enough to allow for some variation within a niche but small enough to maintain separation between niches
- Consider the size of the search space and the expected distance between different subproblems
- Adaptive niche radius techniques can be employed to dynamically adjust the radius based on population characteristics

### Choosing the Crowding Limit
- The crowding limit should be set to maintain a balance between diversity and convergence within each niche
- A higher crowding limit allows for more individuals within a niche but may lead to increased competition and slower convergence
- Experiment with different values and observe the impact on population diversity and convergence speed

### Selecting Genetic Operators
- Choose genetic operators that are suitable for the problem domain and the encoding of individuals
- Crossover operators should be designed to preserve and combine meaningful building blocks from parents
- Mutation operators should introduce sufficient variation to explore the search space effectively

### Defining Termination Criteria
- Consider the desired level of solution quality and the available computational resources
- Set a maximum number of generations or a convergence threshold based on the fitness improvement over consecutive generations
- Optionally, include a runtime limit to prevent excessive computation time

### Handling Overlapping Niches
- If the problem domain has overlapping niches, consider using a more flexible niche definition or a dynamic niche radius
- Encourage collaboration between individuals from overlapping niches through shared fitness evaluation
- Employ techniques like fitness sharing or crowding to maintain diversity in the presence of overlapping niches
