---
title: (μ/ρ +, λ)-Evolution Strategy
---
# (μ/ρ +, λ)-Evolution Strategy

## Name

(μ/ρ +, λ)-Evolution Strategy, (μ/ρ + λ)-ES

## Taxonomy

The (μ/ρ +, λ)-Evolution Strategy is a population-based, stochastic optimization algorithm that falls under the umbrella of Evolutionary Algorithms (EA) and is inspired by biological evolution. It is closely related to other Evolution Strategies like (1+1)-ES, (μ+1)-ES, (μ+λ)-ES, and (μ,λ)-ES.

- Computational Intelligence
  - Biologically Inspired Computation
    - Evolutionary Computation
      - Evolutionary Algorithms
        - Evolution Strategies
          - (μ/ρ +, λ)-Evolution Strategy

## Strategy

### Initialization and Representation

The (μ/ρ +, λ)-ES begins by initializing a population of μ individuals, each representing a potential solution to the optimization problem. These individuals are typically represented as real-valued vectors in the search space. Additionally, each individual is associated with a set of strategy parameters, which control the magnitude and direction of mutations during the search process.

### Parent Selection and Recombination

In each generation, ρ parent individuals are selected from the population of μ individuals. The selection is usually performed uniformly at random, without any bias towards fitness. The selected parents then undergo recombination, where their genetic information is combined to create new offspring individuals. Common recombination operators include intermediate and discrete recombination, which generate offspring by averaging or randomly selecting components from the parent vectors.

### Mutation

After recombination, the λ offspring individuals are subjected to mutation. The mutation operator perturbs the decision variables of each offspring based on the associated strategy parameters. Typically, mutation is performed by adding a normally distributed random vector to the offspring, with the strategy parameters determining the variance of the distribution. The mutated offspring represent new candidate solutions in the search space.

### Survivor Selection

Once the offspring have been generated and mutated, the survivor selection process determines which individuals will survive to the next generation. In the (μ/ρ +, λ)-ES, the survivor selection is performed by combining the μ parent individuals with the λ offspring individuals and selecting the best μ individuals based on their fitness values. This is known as plus selection, as it considers both the parents and offspring for survival.

### Iteration and Termination

The process of parent selection, recombination, mutation, and survivor selection is repeated for a specified number of generations or until a termination criterion is met. The termination criterion can be based on factors such as the maximum number of generations, the convergence of the population, or the achievement of a satisfactory fitness level. Upon termination, the best individual found during the search is returned as the optimized solution.

## Procedure

### Data Structures

- Individual: Represents a candidate solution, consisting of a real-valued vector of decision variables and associated strategy parameters.
- Population: A collection of μ individuals.

### Parameters

- μ: The population size, indicating the number of individuals in the population.
- ρ: The number of parent individuals selected for recombination.
- λ: The number of offspring individuals generated in each generation.
- Recombination Operator: The operator used for combining genetic information from parents (e.g., intermediate or discrete recombination).
- Mutation Operator: The operator used for perturbing the decision variables of offspring individuals.
- Termination Criterion: The condition that determines when the algorithm should stop (e.g., maximum generations, convergence, or fitness threshold).

### Algorithm Steps

1. Initialize a population of μ individuals with random decision variables and strategy parameters.

2. Evaluate the fitness of each individual in the population.

3. While the termination criterion is not met, repeat steps 4-8.

4. Select ρ parent individuals from the population uniformly at random.

5. Apply the recombination operator to the selected parents to generate λ offspring individuals.

6. Apply the mutation operator to each offspring individual, perturbing their decision variables based on the associated strategy parameters.

7. Evaluate the fitness of each offspring individual.

8. Perform survivor selection by combining the μ parent individuals with the λ offspring individuals and selecting the best μ individuals based on their fitness.

9. Return the best individual found during the search as the optimized solution.

## Considerations

### Advantages

- Effective in solving continuous optimization problems with high-dimensional search spaces.
- Robust to noisy and non-convex fitness landscapes.
- Adapts the search step sizes automatically based on the strategy parameters.
- Allows for parallelization and scalability due to the population-based nature of the algorithm.

### Disadvantages

- Requires careful tuning of the population size (μ), parent selection size (ρ), and offspring size (λ) parameters.
- May converge prematurely or stagnate if the diversity of the population is not maintained.
- The choice of recombination and mutation operators can significantly impact the performance of the algorithm.
- Computationally expensive compared to gradient-based optimization methods, especially for large populations and high-dimensional problems.

## Heuristics

### Population Size (μ)

- Start with a population size that is at least 10 times the dimensionality of the problem.
- Increase the population size for more complex or multi-modal fitness landscapes.
- Consider the trade-off between exploration and exploitation when setting the population size.

### Parent Selection Size (ρ)

- Choose a parent selection size that is smaller than the population size (ρ < μ).
- A common heuristic is to set ρ as a fraction of the population size (e.g., ρ = μ/2 or ρ = μ/4).
- Larger values of ρ promote greater diversity in the offspring, while smaller values focus the search around promising regions.

### Offspring Size (λ)

- Set the offspring size to be larger than the population size (λ > μ) to encourage exploration.
- A common heuristic is to set λ as a multiple of the population size (e.g., λ = 7μ or λ = 10μ).
- Larger values of λ increase the computational cost but can improve the quality of the solutions.

### Recombination Operator

- Use intermediate recombination for problems with strong dependencies between decision variables.
- Use discrete recombination for problems with weakly correlated or independent decision variables.
- Experiment with different recombination operators to find the most suitable one for the problem at hand.

### Mutation Operator

- Adapt the mutation step sizes based on the progress of the search (e.g., using self-adaptation or covariance matrix adaptation).
- Use larger mutation step sizes in the early stages of the search to promote exploration and smaller step sizes in the later stages to fine-tune the solutions.
- Consider problem-specific mutation operators that incorporate domain knowledge or constraints.

### Termination Criterion

- Set a maximum number of generations based on the available computational resources and the complexity of the problem.
- Monitor the convergence of the population and stop the algorithm if the fitness improvement stagnates for a certain number of generations.
- Define a target fitness value and terminate the algorithm once a satisfactory solution is found.