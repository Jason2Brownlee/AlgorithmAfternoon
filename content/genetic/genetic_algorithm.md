# Genetic Algorithm

## Name
Genetic Algorithm,  Simple Genetic Algorithm (SGA), Canonical Genetic Algorithm, Basic Genetic Algorithm

## Taxonomy
The Simple Genetic Algorithm is a foundational technique in the field of Evolutionary Computation, which is a subfield of Computational Intelligence. It is closely related to other Evolutionary Algorithms such as Genetic Programming, Evolution Strategies, and Evolutionary Programming.

- Computational Intelligence
  - Biologically Inspired Computation
    - Evolutionary Computation
      - Evolutionary Algorithms
        - Simple Genetic Algorithm

## Strategy
The Simple Genetic Algorithm is based on the principles of natural selection and genetic inheritance. It maintains a population of candidate solutions, each represented as a string of genes (typically binary). The algorithm iteratively evolves the population by applying genetic operators such as selection, crossover, and mutation.

### Selection
In each generation, the algorithm evaluates the fitness of each individual in the population using a problem-specific fitness function. It then selects a subset of the population to serve as parents for the next generation. Common selection methods include tournament selection, where a fixed number of individuals compete based on their fitness, and fitness-proportionate selection, where individuals are chosen with a probability proportional to their relative fitness.

### Crossover
Selected parents are paired up to produce offspring through the crossover operator. Crossover involves exchanging genetic material between the parents to create new individuals. The most common crossover technique is single-point crossover, where a random point is chosen, and the genes beyond that point are swapped between the parents. Other variations include multi-point crossover and uniform crossover.

### Mutation
After crossover, the offspring undergo mutation, where individual genes are randomly altered with a small probability. Mutation introduces new genetic diversity into the population, preventing premature convergence and allowing the algorithm to explore new regions of the search space. In binary representations, mutation typically involves flipping bits.

### Replacement
The newly created offspring are then used to replace a portion of the existing population. Common replacement strategies include generational replacement, where the entire population is replaced by the offspring, and steady-state replacement, where only a few individuals are replaced in each generation.

The process of selection, crossover, mutation, and replacement continues for a specified number of generations or until a termination criterion is met, such as finding a satisfactory solution or reaching a computational budget.

## Procedure
### Data Structures
- Population: An array of individuals, each represented as a string of genes (typically binary).
- Fitness: An array storing the fitness value of each individual in the population.

### Parameters
- Population Size: The number of individuals in the population.
- Crossover Probability: The probability of applying crossover to a pair of parents.
- Mutation Probability: The probability of mutating each gene in an offspring.
- Termination Criterion: The condition for stopping the algorithm, such as a maximum number of generations or a target fitness value.

### Steps
1. Initialize the population
   1. Create an empty population array
   2. For each individual in the population size:
      1. Generate a random string of genes
      2. Add the individual to the population array
2. Evaluate the fitness of each individual in the population
   1. For each individual in the population:
      1. Calculate the fitness value using the problem-specific fitness function
      2. Store the fitness value in the fitness array
3. While the termination criterion is not met:
   1. Select parents from the population
      1. Choose a selection method (e.g., tournament selection or fitness-proportionate selection)
      2. Select a subset of individuals as parents based on their fitness
   2. Create offspring through crossover
      1. Pair up the selected parents
      2. For each pair of parents:
         1. If a random number is less than the crossover probability:
            1. Apply crossover to create two offspring
         2. Else:
            1. Copy the parents as offspring without crossover
   3. Apply mutation to the offspring
      1. For each offspring:
         1. For each gene in the offspring:
            1. If a random number is less than the mutation probability:
               1. Mutate the gene (e.g., flip the bit)
   4. Replace a portion of the population with the offspring
      1. Choose a replacement strategy (e.g., generational or steady-state)
      2. Replace individuals in the population with the offspring based on the chosen strategy
   5. Evaluate the fitness of the new individuals in the population
      1. For each new individual in the population:
         1. Calculate the fitness value using the problem-specific fitness function
         2. Store the fitness value in the fitness array
4. Return the best solution found in the population

## Considerations
### Advantages
- Simplicity: The Simple Genetic Algorithm is relatively easy to understand and implement compared to other optimization techniques.
- Versatility: Genetic Algorithms can be applied to a wide range of optimization problems, including those with discrete, continuous, or mixed-integer variables.
- Robustness: Genetic Algorithms are capable of handling noisy, complex, and multimodal fitness landscapes, making them suitable for problems where traditional optimization methods may struggle.

### Disadvantages
- Parameter Sensitivity: The performance of the Simple Genetic Algorithm can be sensitive to the choice of parameters, such as population size, crossover probability, and mutation probability. Selecting appropriate values for these parameters often requires experimentation and domain knowledge.
- Premature Convergence: If the population loses diversity too quickly, the algorithm may converge to a suboptimal solution. This can occur when the selection pressure is too high or the mutation rate is too low.
- Computational Cost: Genetic Algorithms can be computationally expensive, especially for problems with large search spaces or costly fitness evaluations. The algorithm may require a significant number of generations and fitness evaluations to find a satisfactory solution.

## Heuristics
### Population Size
- Choose a population size that balances exploration and exploitation. A larger population size allows for more diversity and exploration but increases computational cost.
- As a rule of thumb, start with a population size between 50 and 200 individuals and adjust based on the problem complexity and available computational resources.

### Crossover Probability
- Set the crossover probability high enough to promote the exchange of genetic material between individuals. A typical range is between 0.6 and 0.9.
- If the crossover probability is too low, the algorithm may not efficiently combine promising solutions, leading to slow convergence.

### Mutation Probability
- Use a low mutation probability to introduce small amounts of random variation into the population. A common range is between 0.01 and 0.1 per gene.
- If the mutation probability is too high, the algorithm may become too random and fail to converge to a good solution.

### Termination Criterion
- Define a termination criterion that strikes a balance between solution quality and computational resources.
- Common options include setting a maximum number of generations, a target fitness value, or a convergence threshold (e.g., stopping when the best fitness value has not improved for a certain number of generations).

### Fitness Function Design
- Design a fitness function that accurately measures the quality of solutions in the context of the problem being solved.
- Ensure that the fitness function is computationally efficient, as it will be evaluated multiple times during the algorithm's execution.
- Consider normalizing or scaling the fitness values to prevent extreme differences in fitness from dominating the selection process.

### Diversity Maintenance
- Employ techniques to maintain population diversity and prevent premature convergence.
- Options include using a larger population size, increasing the mutation probability, implementing diversity-preserving selection methods (e.g., crowding or niching), or periodically introducing new random individuals into the population.

**Update**: if you need more help, you might be interested in the new [Genetic Algorithm Mini-Book](/books/genetic_algorithm)
