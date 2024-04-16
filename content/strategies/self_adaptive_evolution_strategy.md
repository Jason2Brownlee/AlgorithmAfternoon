# Self-Adaptive Evolution Strategy

## Name
Self-Adaptive Evolution Strategy (SA-ES), Evolution Strategy (ES)

## Taxonomy
The Self-Adaptive Evolution Strategy is a biologically-inspired optimization algorithm that falls under the umbrella of Evolutionary Computation, a subfield of Computational Intelligence. It is closely related to other Evolution Strategies and Evolutionary Algorithms such as the (μ/ρ +, λ)-ES, CMA-ES, and Evolutionary Programming.

- Computational Intelligence
  - Biologically Inspired Computation
    - Evolutionary Computation
      - Evolutionary Algorithms
        - Evolution Strategies
          - Self-Adaptive Evolution Strategy

## Strategy
The Self-Adaptive Evolution Strategy employs principles of biological evolution to iteratively improve a population of candidate solutions for a given optimization problem. The algorithm maintains a population of individuals, each representing a potential solution to the problem at hand. These individuals are encoded as real-valued vectors, often referred to as the genotype or chromosome.

### Mutation and Recombination
In each iteration (generation) of the algorithm, the individuals undergo mutation and recombination operations to create offspring. Mutation introduces random perturbations to the individuals' genetic material, enabling exploration of the search space. Recombination, on the other hand, combines genetic information from multiple parents to create new offspring, promoting the exploitation of promising solutions.

### Self-Adaptation of Strategy Parameters
A key feature of the Self-Adaptive Evolution Strategy is the self-adaptation of strategy parameters, such as the mutation step sizes. Each individual not only carries the object variables (i.e., the solution encoding) but also the strategy parameters. These parameters are subject to mutation and recombination alongside the object variables, allowing the algorithm to adapt its search behavior during the optimization process.

### Selection and Replacement
After the offspring are generated, a selection mechanism is applied to determine which individuals survive into the next generation. The Self-Adaptive Evolution Strategy typically employs a (μ, λ) or (μ + λ) selection scheme, where μ denotes the number of parents and λ represents the number of offspring. In the (μ, λ) scheme, the best μ offspring replace the parents, while in the (μ + λ) scheme, the best μ individuals are selected from the combined pool of parents and offspring.

### Termination
The process of mutation, recombination, and selection continues iteratively until a termination criterion is met. Common termination criteria include reaching a maximum number of generations, achieving a satisfactory fitness level, or observing convergence of the population.

## Procedure
1. Initialize the population
   1. Set the population size (μ) and the number of offspring (λ)
   2. Randomly initialize μ individuals, each consisting of object variables and strategy parameters
2. While termination criteria are not met, do:
   1. Recombination
      1. Select ρ parents from the population
      2. Perform recombination on the object variables and strategy parameters of the selected parents to create λ offspring
   2. Mutation
      1. For each offspring, mutate the strategy parameters
      2. For each offspring, mutate the object variables using the mutated strategy parameters
   3. Evaluation
      1. Evaluate the fitness of each offspring
   4. Selection
      1. Select the best μ individuals from the offspring (for (μ, λ) selection) or from the combined pool of parents and offspring (for (μ + λ) selection)
      2. Replace the parent population with the selected individuals
3. Return the best individual found

### Data Structures
- Individual: Represents a candidate solution, consisting of object variables and strategy parameters
- Population: A collection of individuals

### Parameters
- μ: The number of parent individuals in the population
- λ: The number of offspring generated in each generation
- ρ: The number of parents selected for recombination
- Mutation strength: Controls the magnitude of mutations applied to the object variables and strategy parameters
- Recombination type: Defines the method used for recombining parent individuals (e.g., discrete, intermediate)

## Considerations
### Advantages
- Self-adaptation of strategy parameters allows the algorithm to automatically adjust its search behavior during the optimization process
- Effective in solving continuous optimization problems
- Robust to local optima and able to escape suboptimal regions of the search space

### Disadvantages
- Performance may be sensitive to the choice of initial strategy parameters
- Requires a relatively large number of fitness evaluations compared to some other optimization methods
- The self-adaptation mechanism introduces additional complexity to the algorithm

## Heuristics
### Population Size
- The population size (μ) should be large enough to maintain diversity but not so large that it hinders convergence
- A common heuristic is to set μ proportional to the problem dimensionality (e.g., 4 + ⌊3ln(n)⌋, where n is the number of object variables)

### Offspring Size
- The number of offspring (λ) is typically set to be larger than the population size (μ)
- A recommended ratio is λ = 7μ

### Selection Scheme
- The (μ, λ) selection scheme is generally preferred for faster convergence
- The (μ + λ) selection scheme can be used for problems with changing fitness landscapes or when a larger degree of exploration is desired

### Mutation Strength
- The initial mutation strengths should be set based on the expected range of the object variables
- Mutation strengths can be initialized as a fraction of the search space size (e.g., 1/10th of the variable range)
- The mutation strengths should be allowed to adapt during the optimization process

### Recombination
- Intermediate recombination is commonly used for the object variables and strategy parameters
- The number of parents for recombination (ρ) is typically set to 2

### Termination Criteria
- Define a maximum number of generations based on the available computational budget
- Monitor the progress of the best fitness value and stop if no significant improvement is observed over a predefined number of generations
- Check for convergence of the population by measuring the diversity of the individuals (e.g., using standard deviation of fitness values)
