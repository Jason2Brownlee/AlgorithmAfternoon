# Automatic Function Definition Genetic Programming

## Name
Automatic Function Definition Genetic Programming (AFDGP)

## Taxonomy
Automatic Function Definition Genetic Programming (AFDGP) is a variant of Genetic Programming (GP) that automatically defines and evolves reusable functions during the evolutionary process. It is closely related to Modular Genetic Programming and Adaptive Representation Genetic Programming.

- Artificial Intelligence
  - Computational Intelligence
    - Biologically Inspired Computation
      - Evolutionary Computation
        - Genetic Programming (GP)
          - Automatic Function Definition Genetic Programming (AFDGP)

## Strategy
AFDGP extends the standard Genetic Programming model by introducing the concept of automatically defined functions (ADFs). ADFs are evolved alongside the main program tree and can be called from within the main program or other ADFs. This allows for the reuse of useful code fragments and the evolution of modular solutions.

The evolutionary process in AFDGP begins with a population of individuals, each representing a program composed of a main tree and a set of ADFs. The main tree and ADFs are evolved simultaneously using genetic operators such as crossover and mutation. The fitness of each individual is evaluated based on its performance on a given problem.

During the evolution process, the ADFs can be called from the main program tree or other ADFs, allowing for the creation of hierarchical and modular solutions. The evolutionary process encourages the reuse of useful code fragments by promoting the survival and propagation of individuals with well-performing ADFs.

## Procedure
### Data Structures
- Function Set: A set of primitive functions and operators used to construct the program trees.
- Terminal Set: A set of variables and constants used as leaf nodes in the program trees.
- Individual: A structure representing a candidate solution, which consists of:
  - Main Program Tree: A tree structure representing the main program.
  - Automatically Defined Functions (ADFs): An array of tree structures representing the automatically defined functions.
  - Fitness: The fitness value of the individual.
- Population: An array of individuals.

### Parameters
- Population Size: The number of individuals in the population.
- Maximum Number of Generations: The maximum number of generations to run the algorithm.
- Crossover Probability: The probability of applying the crossover operator to create offspring.
- Mutation Probability: The probability of applying the mutation operator to modify an individual.
- Maximum Tree Depth: The maximum allowed depth of the program trees.
- Maximum Number of ADFs: The maximum number of automatically defined functions allowed per individual.

### Steps
1. Initialize the population
   1. For each individual in the population:
      1. Create the main program tree
         1. Randomly generate a program tree using the function set and terminal set.
         2. Ensure that the depth of the tree does not exceed the maximum tree depth.
      2. Create the automatically defined functions (ADFs)
         1. For each ADF (up to the maximum number of ADFs):
            1. Randomly generate a program tree using the function set and terminal set.
            2. Ensure that the depth of the tree does not exceed the maximum tree depth.
      3. Evaluate the fitness of the individual.
2. For each generation until the maximum number of generations is reached:
   1. Create a new population
      1. While the new population is not full:
         1. Select parent individuals using a selection method (e.g., tournament selection).
         2. Create offspring using genetic operators
            1. If a random number is less than the crossover probability:
               1. Apply the crossover operator to the selected parents.
                  1. Randomly select crossover points in the main program trees and ADF trees of the parents.
                  2. Exchange the subtrees at the selected crossover points between the parents to create two offspring.
            2. If a random number is less than the mutation probability:
               1. Apply the mutation operator to the offspring.
                  1. Randomly select mutation points in the main program trees and ADF trees of the offspring.
                  2. Replace the subtrees at the selected mutation points with randomly generated subtrees.
         3. Evaluate the fitness of the offspring.
         4. Add the offspring to the new population.
   2. Replace the old population with the new population.
3. Return the best individual found in the population.


## Considerations
Advantages:
- Enables the automatic discovery and reuse of useful code fragments.
- Promotes the evolution of modular and hierarchical solutions.
- Can lead to more compact and interpretable solutions compared to standard GP.

Disadvantages:
- Increased complexity due to the management of ADFs.
- Higher computational cost compared to standard GP.
- The optimal number and structure of ADFs may be problem-dependent.

## Heuristics
### Parameter Settings
- Set the population size based on the problem complexity. A larger population size can help maintain diversity but increases computational cost.
- Adjust the maximum number of generations based on the available computational resources and the problem's difficulty.
- Set the crossover and mutation probabilities to balance exploration and exploitation. Typical values range from 0.7 to 0.9 for crossover and 0.01 to 0.1 for mutation.
- Limit the maximum tree depth to prevent the evolution of overly complex solutions. A depth of 5 to 10 is often sufficient.
- Start with a small number of ADFs (e.g., 1 to 3) and gradually increase if needed. Too many ADFs can lead to bloat and reduced interpretability.

### Function and Terminal Sets
- Include problem-specific functions and terminals in the main tree and ADFs.
- Ensure that the function and terminal sets are sufficiently expressive to solve the problem at hand.
- Consider including higher-level primitives or domain-specific operators to improve solution quality and convergence speed.

### ADF Management
- Encourage the reuse of ADFs by incorporating a fitness bonus for individuals that effectively utilize ADFs.
- Implement mechanisms to prevent the excessive growth of ADFs, such as a size limit or a parsimony pressure.
- Allow the evolution of ADFs with different arities (number of arguments) to enhance flexibility and adaptability.

### Diversity Maintenance
- Employ techniques like speciation or niching to maintain population diversity and prevent premature convergence.
- Consider using a multi-objective approach to balance solution fitness and diversity.

### Problem-Specific Adaptations
- Tailor the fitness function to effectively capture the desired behavior and guide the evolutionary process.
- Incorporate domain knowledge or problem-specific heuristics to improve the search efficiency and solution quality.
- Experiment with different representations or extensions of AFDGP, such as strongly typed GP or grammatical evolution, if suitable for the problem domain.