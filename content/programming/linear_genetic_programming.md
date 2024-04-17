# Linear Genetic Programming

## Name

Linear Genetic Programming (LGP)

## Taxonomy

Linear Genetic Programming is a variant of Genetic Programming (GP) that belongs to the field of Evolutionary Computation, a subfield of Computational Intelligence. LGP is closely related to traditional tree-based GP and other variants such as Cartesian Genetic Programming (CGP) and Grammatical Evolution (GE).

- Computational Intelligence
  - Evolutionary Computation
    - Evolutionary Algorithms
      - Genetic Algorithms
      - Evolutionary Strategies
      - Genetic Programming
        - Tree-based Genetic Programming
        - Linear Genetic Programming
        - Cartesian Genetic Programming
        - Grammatical Evolution

## Strategy

### Representation

In Linear Genetic Programming, programs are represented as linear sequences of instructions, similar to machine code or assembly language. Each instruction consists of an operator (function) and one or more operands (terminals). The instructions are executed sequentially, with the output of one instruction serving as the input to the next.

### Initialization

The initial population of programs is generated randomly. Each program is created by randomly selecting instructions from the available set of operators and terminals, and arranging them in a linear sequence. The length of the programs may be fixed or variable, depending on the specific implementation.

### Evaluation

Each program in the population is evaluated based on its performance on a given problem. The fitness of a program is typically determined by executing it on a set of test cases and measuring how well it solves the problem. The specific fitness function depends on the nature of the problem being solved.

### Selection

After evaluating the population, a selection mechanism is used to choose parents for reproduction. Common selection methods include tournament selection, where a subset of individuals compete based on their fitness, and fitness-proportionate selection, where individuals are chosen with a probability proportional to their fitness.

### Variation Operators

Linear Genetic Programming uses two main variation operators to create new programs: crossover and mutation.

Crossover involves combining genetic material from two parent programs to create one or more offspring. In LGP, this is typically achieved by selecting a random crossover point in each parent and swapping the instructions beyond that point.

Mutation introduces random changes into a program. This can involve replacing an instruction with a randomly generated one, swapping the positions of two instructions, or modifying the operands of an instruction.

### Replacement

After creating a new generation of programs through selection and variation, the population is updated by replacing some or all of the existing individuals with the newly generated ones. This can be done using various replacement strategies, such as generational replacement (replacing the entire population) or steady-state replacement (replacing a subset of the population).

## Procedure

### Data Structures

- Individual: Represents a single program in the population, consisting of a linear sequence of instructions.
- Instruction: Consists of an operator and one or more operands.
- Population: A collection of individuals.

### Parameters

- Population Size: The number of individuals in the population.
- Max Generations: The maximum number of generations to run the algorithm.
- Crossover Rate: The probability of applying crossover to a pair of selected parents.
- Mutation Rate: The probability of applying mutation to an individual.
- Tournament Size: The number of individuals participating in tournament selection.
- Instruction Set: The available operators and terminals used to construct programs.

### Pseudocode

1. Initialize the population with random individuals
2. Evaluate the fitness of each individual in the population
3. While termination criteria are not met (e.g., max generations):
   1. Select parents using a selection mechanism (e.g., tournament selection)
   2. For each pair of parents:
      1. With probability crossover_rate, perform crossover to create offspring
      2. With probability mutation_rate, apply mutation to the offspring
   3. Evaluate the fitness of the new offspring
   4. Replace individuals in the population with the offspring based on a replacement strategy
4. Return the best individual found

## Considerations

### Advantages

- Flexible representation: LGP can express a wide range of programs and is not limited by a predefined tree structure.
- Efficient execution: Linear programs can be executed quickly, as they do not require parsing a tree structure.
- Modularity: Instructions can be reused and combined in different ways to solve complex problems.

### Disadvantages

- Bloat: Like other GP variants, LGP can suffer from code bloat, where programs become unnecessarily large.
- Limited expressiveness: Some problems may be more naturally expressed using a tree or graph structure, which can be challenging to represent in a linear format.
- Parameter sensitivity: The performance of LGP can be sensitive to the choice of parameters, such as population size and variation operator rates.

## Heuristics

### Population Size

- Use a population size that provides sufficient diversity while keeping computational costs manageable.
- Typical population sizes range from 50 to 1000 individuals, depending on the problem complexity.

### Variation Operator Rates

- Set the crossover rate high enough to promote exploration of new program combinations, typically between 0.5 and 1.0.
- Use a low mutation rate to introduce minor variations without disrupting good solutions, typically between 0.01 and 0.1.

### Instruction Set Design

- Include a diverse set of operators and terminals that are relevant to the problem domain.
- Ensure that the instruction set is expressive enough to solve the problem but not overly complex, which can slow down evolution.

### Termination Criteria

- Set a maximum number of generations based on the available computational resources and the problem complexity.
- Consider using early stopping criteria, such as terminating when the fitness improvement stagnates for a certain number of generations.

### Elitism

- Preserve a small number of the best individuals from each generation to prevent the loss of good solutions.
- Elitism can help accelerate convergence and maintain the best solutions found throughout the evolution process.

