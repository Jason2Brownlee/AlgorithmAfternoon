# Cartesian Genetic Programming

## Name
Cartesian Genetic Programming (CGP)

## Taxonomy
Cartesian Genetic Programming is an evolutionary algorithm that belongs to the field of Genetic Programming, which is a subfield of Evolutionary Computation, a branch of Computational Intelligence.

- Computational Intelligence
  - Evolutionary Computation
    - Evolutionary Algorithms
      - Genetic Algorithms
      - Evolution Strategies
      - Evolutionary Programming
      - Genetic Programming
        - Tree-based GP
        - Linear GP
        - Graph-based GP
          - Cartesian Genetic Programming

## Strategy
CGP represents computational structures as directed acyclic graphs encoded in Cartesian coordinates of nodes. The genotype encodes the program graph, where each node represents a particular function, and the edges between nodes represent the flow of data. The genotype is a fixed-length representation, which allows for a bounded complexity of the evolved programs.

The evolutionary process in CGP involves the repeated application of genetic operators, such as mutation and crossover, to a population of individuals. The fitness of each individual is evaluated based on its performance on a given task, and the fittest individuals are selected for reproduction, creating the next generation of the population.

One key feature of CGP is its implicit redundancy, where some nodes in the genotype may not be connected to the output nodes and thus do not contribute to the final program. This redundancy allows for neutral mutations, which can help maintain genetic diversity and facilitate the exploration of the search space.

## Procedure
Data Structures:
- Genotype: A fixed-length integer array representing the program graph, where each gene encodes the function and connections of a node.
- Phenotype: The actual program graph that is decoded from the genotype and executed to solve the given problem.

Parameters:
- Population size: The number of individuals in each generation.
- Mutation rate: The probability of a gene being mutated during reproduction.
- Number of generations: The maximum number of iterations of the evolutionary process.
- Function set: The set of primitive functions used to construct the program graphs.

Procedure:
1. Initialization:
   1. Create an initial population of individuals with randomly generated genotypes.
   2. Decode each genotype into its corresponding phenotype (program graph).
   3. Evaluate the fitness of each individual by executing its phenotype on the given problem.

2. Evolution:
   1. Select parents for reproduction based on their fitness (e.g., tournament selection).
   2. Create offspring by applying genetic operators to the selected parents:
      1. Mutation: Randomly modify genes in the genotype with a given mutation rate.
      2. Crossover (optional): Exchange genetic material between two parent genotypes to create offspring.
   3. Decode the offspring genotypes into their corresponding phenotypes.
   4. Evaluate the fitness of the offspring by executing their phenotypes on the given problem.
   5. Replace the least fit individuals in the population with the offspring.

3. Termination:
   1. Repeat the evolution process (step 2) until a termination criterion is met, such as reaching a maximum number of generations or finding a solution with satisfactory fitness.
   2. Return the best individual (program graph) found during the evolution process as the solution to the problem.

## Considerations
Advantages:
- Flexible representation: CGP can represent a wide range of computational structures and can be applied to various domains, such as circuit design, image processing, and machine learning.
- Implicit redundancy: The presence of inactive nodes in the genotype allows for neutral mutations, which can help maintain genetic diversity and facilitate the exploration of the search space.
- Scalability: CGP can evolve complex programs with a fixed-length genotype, making it computationally efficient and scalable to larger problem instances.

Disadvantages:
- Genotype-phenotype mapping: The mapping between the genotype and phenotype in CGP can be complex, which may make it difficult to interpret and analyze the evolved programs.
- Parameter sensitivity: The performance of CGP can be sensitive to the choice of parameters, such as the mutation rate and the size of the function set, requiring careful tuning for each problem.
- Limited crossover effectiveness: Crossover operators may not be as effective in CGP compared to other evolutionary algorithms due to the fixed-length genotype and the potential disruption of important subgraphs.

## Heuristics
Function Set Selection:
- Choose a function set that is expressive enough to solve the given problem but not overly complex to avoid unnecessary computational overhead.
- Include functions that are relevant to the problem domain and can capture important features or patterns in the data.
- Consider using a mix of arithmetic, logical, and domain-specific functions to allow for a diverse range of program structures.

Mutation Rate:
- Start with a mutation rate between 1% and 5% and adjust based on the problem complexity and the desired balance between exploration and exploitation.
- Higher mutation rates can help maintain genetic diversity and prevent premature convergence but may slow down the convergence to optimal solutions.
- Lower mutation rates can lead to faster convergence but may increase the risk of getting stuck in local optima.

Population Size:
- Use a population size that is large enough to maintain genetic diversity and explore the search space effectively but not so large as to significantly increase the computational cost.
- A typical population size for CGP ranges from 50 to 1000 individuals, depending on the problem complexity and available computational resources.
- Consider using a smaller population size with a larger number of generations for problems with a smooth fitness landscape and a larger population size with fewer generations for problems with a rugged fitness landscape.

Genotype Length:
- Choose a genotype length that allows for sufficient complexity in the evolved programs to solve the given problem but not so large as to increase the search space unnecessarily.
- Start with a genotype length that is a multiple of the number of inputs and outputs in the problem and adjust based on the desired program complexity.
- Consider using a dynamic genotype length that can be increased or decreased during the evolution process based on the fitness of the individuals or the progress of the search.
