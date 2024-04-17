# Gene Expression Programming

## Name

Gene Expression Programming (GEP)

## Taxonomy

Gene Expression Programming is a branch of Evolutionary Computation, which falls under the umbrella of Computational Intelligence and Biologically Inspired Computation. It is closely related to Genetic Programming (GP) and Genetic Algorithms (GA).

- Computational Intelligence
  - Biologically Inspired Computation
    - Evolutionary Computation
      - Evolutionary Algorithms
        - Genetic Algorithms (GA)
        - Genetic Programming (GP)
          - Gene Expression Programming (GEP)

## Strategy

Gene Expression Programming is an evolutionary algorithm that evolves computer programs or mathematical expressions to solve a given problem. The key difference between GEP and other evolutionary algorithms like GP is the separation of genotype and phenotype.

### Genotype-Phenotype Separation

In GEP, individuals are encoded as linear strings of fixed length (genotype), which are then translated into expression trees (phenotype) of different sizes and shapes. This separation allows for the creation of multiple genes, each encoding a sub-expression tree. The genes are then linked together to form a more complex multi-subunit expression.

### Genetic Operators

GEP employs genetic operators similar to those used in GA and GP, such as mutation, transposition, and recombination. These operators are applied to the linear genotype, which is then translated into the expression tree for fitness evaluation.

### Fitness Evaluation

The fitness of each individual is evaluated based on how well the expression tree solves the given problem. This is typically done by executing the expression tree on a set of training data and measuring the error or deviation from the expected output.

### Selection and Reproduction

Individuals are selected for reproduction based on their fitness, with higher-fitness individuals having a greater chance of being selected. The selected individuals then undergo genetic operations to create the next generation of candidate solutions.

## Procedure

### Data Structures

- Chromosome: A linear string of fixed length representing the genotype of an individual.
- Gene: A substring of the chromosome that encodes an expression tree.
- Expression Tree: A tree-like structure representing the phenotype of an individual, which can be executed to solve the problem.

### Parameters

- Population Size: The number of individuals in each generation.
- Number of Generations: The maximum number of iterations the algorithm will run.
- Mutation Rate: The probability of a gene undergoing mutation.
- Transposition Rate: The probability of a gene undergoing transposition.
- Recombination Rate: The probability of two individuals exchanging genetic material.

### Algorithm Steps

1. Initialize the population with random chromosomes.
2. While the termination criteria are not met, do:
   1. For each individual in the population:
      1. Translate the chromosome into an expression tree.
      2. Execute the expression tree on the training data.
      3. Calculate the fitness of the individual based on its performance.
   2. Select individuals for reproduction based on their fitness.
   3. Apply genetic operators (mutation, transposition, recombination) to the selected individuals to create a new generation.
   4. Replace the current population with the new generation.
3. Return the best individual found during the search.

## Considerations

### Advantages

- Separates genotype and phenotype, allowing for more flexible and efficient search.
- Can evolve complex, multi-subunit expressions.
- Employs a simple, linear genotype representation.

### Disadvantages

- Requires careful design of the function and terminal sets for the problem domain.
- May suffer from bloat, where the size of the expressions grows without a corresponding improvement in fitness.
- Can be computationally expensive, especially for large populations and long chromosomes.

## Heuristics

### Function and Terminal Sets

- Choose functions and terminals that are relevant and sufficient for the problem domain.
- Include a diverse set of functions to allow for the evolution of complex expressions.
- Ensure the function and terminal sets are closed, meaning that any function can accept as input the output of any other function or terminal.

### Population Size and Generations

- Use a population size that balances diversity and computational efficiency. Typical values range from 50 to 1000 individuals.
- Set the number of generations based on the complexity of the problem and the available computational resources. Monitor the fitness progress to determine if additional generations are needed.

### Genetic Operator Rates

- Start with a mutation rate around 0.1 and adjust based on the problem and population diversity.
- Use a lower transposition rate, around 0.05, to introduce small variations in the expression structure.
- Set the recombination rate around 0.7 to encourage the exchange of genetic material between individuals.

### Fitness Function

- Design a fitness function that accurately measures the performance of the individuals on the problem.
- Consider using a multi-objective fitness function to balance multiple criteria, such as accuracy and expression complexity.
- Normalize the fitness values to ensure a fair comparison between individuals.

### Termination Criteria

- Set a maximum number of generations as a stopping condition to prevent indefinite running.
- Monitor the fitness progress and stop the algorithm if no significant improvement is observed over a certain number of generations.
- Include a target fitness value as a termination criterion, stopping the algorithm once an individual reaches or exceeds this value.
