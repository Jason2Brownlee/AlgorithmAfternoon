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
Data Structures:
- Individual: Represents a program composed of a main tree and a set of ADFs.
- Main Tree: The primary program tree that represents the overall solution.
- ADF: An automatically defined function that can be called from the main tree or other ADFs.
- Population: A collection of individuals in the current generation.

Parameters:
- Population Size: The number of individuals in each generation.
- Max Generations: The maximum number of generations to evolve.
- Crossover Probability: The probability of applying crossover to selected individuals.
- Mutation Probability: The probability of applying mutation to selected individuals.
- Max Tree Depth: The maximum depth allowed for the main tree and ADFs.
- Number of ADFs: The number of automatically defined functions to evolve.

Pseudocode:
1. Initialize the population with randomly generated individuals.
   1.1. For each individual:
      1.1.1. Create a main tree with random program primitives.
      1.1.2. Create a set of ADFs with random program primitives.
2. Evaluate the fitness of each individual in the population.
3. Repeat until the maximum number of generations is reached or a satisfactory solution is found:
   3.1. Select parents from the population based on their fitness.
   3.2. Create new offspring by applying genetic operators:
      3.2.1. Crossover:
         3.2.1.1. With a given probability, select two parents.
         3.2.1.2. Swap randomly selected subtrees between the main trees of the parents.
         3.2.1.3. Swap randomly selected subtrees between the corresponding ADFs of the parents.
      3.2.2. Mutation:
         3.2.2.1. With a given probability, select an individual.
         3.2.2.2. Randomly select a subtree in the main tree or an ADF.
         3.2.2.3. Replace the selected subtree with a randomly generated subtree.
   3.3. Evaluate the fitness of the new offspring.
   3.4. Replace the population with the new offspring.
4. Return the best individual found during the evolution process.

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