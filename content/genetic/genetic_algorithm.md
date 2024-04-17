# Genetic Algorithm

## Name

Genetic Algorithm, GA, Genetic Optimization, Genetic Search

## Taxonomy

Genetic Algorithms are a class of Evolutionary Algorithms, which are a subfield of Computational Intelligence and Biologically Inspired Computation, used for optimization and search problems. They are closely related to other Evolutionary Algorithms such as Evolution Strategies, Evolutionary Programming, and Genetic Programming.

- Computational Intelligence
  - Biologically Inspired Computation
    - Evolutionary Computation
      - Evolutionary Algorithms
        - Genetic Algorithms

## Strategy

### Population-based Search

Genetic Algorithms maintain a population of candidate solutions, often referred to as individuals or chromosomes. Each individual represents a potential solution to the problem at hand. The population evolves over generations, with the fittest individuals surviving and reproducing, leading to increasingly better solutions.

### Fitness Evaluation

The quality of each individual in the population is evaluated using a fitness function. The fitness function assigns a score to each individual based on how well it solves the problem. This fitness score guides the selection process, favoring the survival and reproduction of fitter individuals.

### Genetic Operators

Genetic Algorithms employ genetic operators inspired by biological evolution to create new individuals:

- Selection: Fitter individuals are selected to become parents for the next generation. Common selection methods include tournament selection, roulette wheel selection, and rank-based selection.

- Crossover: Selected parents are combined to create offspring that inherit traits from both parents. Crossover operators exchange genetic material between parents, enabling the exploration of new solutions. Common crossover techniques include one-point crossover, two-point crossover, and uniform crossover.

- Mutation: After crossover, offspring may undergo random mutations that introduce small changes to their genetic material. Mutation helps maintain diversity in the population and allows the exploration of new areas in the search space.

### Generational Replacement

After the creation of offspring through selection, crossover, and mutation, the new individuals are added to the population. The population size is typically kept constant, so a portion of the previous generation is replaced by the new offspring. This process continues for a specified number of generations or until a satisfactory solution is found.

## Procedure

1. Initialize the population:
   1. Determine the population size and the representation of individuals (e.g., binary strings, real-valued vectors).
   2. Create a population of random individuals.

2. Evaluate the fitness of each individual in the population using the fitness function.

3. Repeat until the termination condition is met (e.g., maximum number of generations, satisfactory solution found):
   1. Selection:
      1. Select parents from the population based on their fitness scores.
      2. Common selection methods: tournament selection, roulette wheel selection, rank-based selection.
   2. Crossover:
      1. Perform crossover on the selected parents to create offspring.
      2. Common crossover techniques: one-point crossover, two-point crossover, uniform crossover.
   3. Mutation:
      1. Apply mutation to the offspring with a certain probability.
      2. Mutation introduces small random changes to the genetic material of the offspring.
   4. Evaluate the fitness of the new offspring using the fitness function.
   5. Replace a portion of the population with the new offspring.

4. Return the best solution found.

### Data Structures and Parameters

- Population: An array or list of individuals representing candidate solutions.
- Individual: Represents a single solution, typically encoded as a binary string, real-valued vector, or other suitable representation.
- Fitness Function: Evaluates the quality of an individual and assigns a fitness score.
- Population Size: The number of individuals in the population.
- Crossover Probability: The probability of applying crossover to selected parents.
- Mutation Probability: The probability of applying mutation to an offspring.
- Termination Condition: Determines when the algorithm should stop (e.g., maximum number of generations, satisfactory solution found).

## Considerations

### Advantages

- Adaptability: Genetic Algorithms can be applied to a wide range of optimization problems, including those with complex, non-linear, and multimodal search spaces.
- Robustness: They are less susceptible to getting stuck in local optima compared to gradient-based optimization methods.
- Parallelizability: Genetic Algorithms are inherently parallel and can be easily distributed across multiple processors or machines for improved performance.

### Disadvantages

- Parameter Tuning: Genetic Algorithms require careful tuning of various parameters, such as population size, crossover and mutation probabilities, to achieve optimal performance for a specific problem.
- Computational Cost: Evaluating the fitness of individuals can be computationally expensive, especially for large populations and complex problems.
- Premature Convergence: If the selection pressure is too high or the population diversity is not maintained, Genetic Algorithms may converge prematurely to suboptimal solutions.

## Heuristics

### Population Size

- Start with a population size that is not too small to avoid premature convergence and not too large to avoid excessive computational cost.
- A common heuristic is to use a population size that is 10 times the number of variables or dimensions in the problem.
- Experiment with different population sizes and observe the convergence behavior and solution quality.

### Selection Method

- Tournament selection is a popular choice due to its simplicity and effectiveness. It selects the best individual from a randomly chosen subset of the population.
- Roulette wheel selection assigns selection probabilities proportional to the fitness scores of individuals, favoring fitter individuals.
- Rank-based selection assigns selection probabilities based on the rank of individuals in the population, reducing the influence of extreme fitness values.

### Crossover and Mutation Probabilities

- Crossover probability typically ranges from 0.6 to 0.9. Higher values promote exploration of new solutions, while lower values focus on exploitation of existing solutions.
- Mutation probability is usually set to a low value, often in the range of 0.01 to 0.1, to introduce small variations without disrupting the overall structure of the solutions.
- Adaptively adjusting the crossover and mutation probabilities based on the progress of the search can help balance exploration and exploitation.

### Termination Condition

- Set a maximum number of generations as a termination condition to prevent the algorithm from running indefinitely.
- Monitor the progress of the best fitness value over generations and terminate if no significant improvement is observed for a certain number of generations.
- Define a target fitness value or acceptable solution quality as a termination condition if the problem's optimal solution or desired performance is known.

### Representation and Operators

- Choose a representation that naturally encodes the problem's variables and constraints, such as binary strings for discrete problems or real-valued vectors for continuous problems.
- Design crossover and mutation operators that respect the problem's constraints and produce valid offspring.
- Consider using problem-specific heuristics or local search techniques to improve the quality of solutions generated by the genetic operators.

### Diversity Maintenance

- Incorporate mechanisms to maintain population diversity, such as niching, crowding, or fitness sharing, to prevent premature convergence and explore multiple optima.
- Introduce new randomly generated individuals into the population at regular intervals to inject fresh genetic material and promote exploration.

