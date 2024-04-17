---
title: DE/rand/1/bin
---
# DE/rand/1/bin

## Name

DE/rand/1/bin, Differential Evolution, rand/1/bin

## Taxonomy

Differential Evolution (DE) is a stochastic optimization algorithm belonging to the field of Evolutionary Computation, a subfield of Computational Intelligence. It is closely related to other population-based metaheuristics such as Genetic Algorithms and Evolutionary Strategies.

- Computational Intelligence
  - Biologically Inspired Computation
    - Evolutionary Computation
      - Evolutionary Algorithms
        - Genetic Algorithms
        - Evolutionary Programming
        - Evolutionary Strategies
        - Differential Evolution
          - DE/rand/1/bin

## Strategy

Differential Evolution is a population-based optimization technique that iteratively improves a set of candidate solutions, called individuals, by applying simple mathematical operations inspired by biological evolution. The algorithm maintains a population of individuals, each representing a potential solution to the problem at hand. At each generation, DE creates new individuals by combining existing ones using a differential mutation operator and a crossover operator. The mutation operator randomly selects three distinct individuals from the population and adds a scaled difference vector between two of them to the third, creating a mutant vector. The crossover operator then combines elements from the mutant vector and the corresponding target vector to produce a trial vector. Finally, the trial vector competes with the target vector, and the better one survives into the next generation.

### Differential Mutation

The differential mutation operator is the key component of DE. For each target vector in the population, it randomly selects three other distinct individuals and creates a mutant vector by adding the scaled difference between two of them to the third. The scaling factor, denoted as F, controls the amplification of the differential variation.

### Crossover

After mutation, DE applies a crossover operator to enhance diversity. The most commonly used crossover strategy is binomial crossover (DE/rand/1/bin), where each element of the trial vector is inherited from either the mutant vector or the target vector based on a crossover probability, denoted as CR. This operator balances exploration and exploitation by introducing new information while preserving some of the characteristics of the target vector.

### Selection

The selection operator in DE is a simple one-to-one competition between the trial vector and the corresponding target vector. If the trial vector has an equal or better objective function value than the target vector, it replaces the target vector in the population; otherwise, the target vector is retained. This greedy selection strategy ensures that the population quality never deteriorates over generations.

## Procedure

Data Structures:
- Population: A set of candidate solutions, each represented as a D-dimensional real-valued vector.
- Mutant Vector: A vector created by the differential mutation operator.
- Trial Vector: A vector created by the crossover operator, combining elements from the mutant vector and the target vector.

Parameters:
- Population Size (NP): The number of individuals in the population.
- Crossover Probability (CR): The probability of inheriting an element from the mutant vector during crossover.
- Scaling Factor (F): The factor used to control the amplification of the differential variation during mutation.

Procedure:
1. Initialization:
   1. Set the values of NP, CR, and F.
   2. Randomly initialize a population of NP individuals within the search space bounds.
2. While the termination criterion is not met, do:
   1. For each target vector in the population, do:
      1. Mutation:
         1. Randomly select three distinct individuals from the population, different from the target vector.
         2. Create a mutant vector by adding the scaled difference between two of the selected individuals to the third.
      2. Crossover:
         1. Create a trial vector by combining elements from the mutant vector and the target vector based on CR.
         2. For each dimension of the trial vector, do:
            1. Generate a random number between 0 and 1.
            2. If the random number is less than or equal to CR or the current dimension is a randomly chosen index, inherit the corresponding element from the mutant vector; otherwise, inherit from the target vector.
      3. Selection:
         1. Evaluate the objective function value of the trial vector.
         2. If the trial vector has an equal or better objective function value than the target vector, replace the target vector with the trial vector in the population; otherwise, keep the target vector.
3. Return the best solution found in the population.

## Considerations

Advantages:
- Simple and easy to implement, with few control parameters.
- Effective in solving a wide range of optimization problems, including non-differentiable, nonlinear, and multimodal functions.
- Exhibits good convergence properties and requires minimal problem-specific parameter tuning.

Disadvantages:
- Performance may deteriorate in high-dimensional search spaces due to the increased complexity of the landscape.
- Convergence speed can be slow, especially for complex problems with many local optima.
- Lack of explicit mechanism for preserving diversity may lead to premature convergence in some cases.

## Heuristics

### Population Size (NP)
- As a rule of thumb, set NP to be about 5 to 10 times the dimensionality of the problem.
- Larger populations can improve exploration and prevent premature convergence but increase computational cost.
- Smaller populations may converge faster but risk getting stuck in suboptimal solutions.

### Crossover Probability (CR)
- CR controls the balance between exploration and exploitation. Higher values favor exploration, while lower values emphasize exploitation.
- A common starting point is CR = 0.5, which gives equal importance to both the mutant and target vectors.
- Adjust CR based on the problem characteristics. For separable problems, lower CR values (0.1 to 0.2) can be effective, while for non-separable problems, higher values (0.9 to 1.0) may work better.

### Scaling Factor (F)
- F controls the magnitude of the differential variation. Higher values increase the step size, while lower values make the search more conservative.
- Typically, F is set between 0.4 and 1.0. A good initial value is often around 0.5.
- Smaller F values are suitable for unimodal problems or when the population is close to the optimum, while larger values can help escape local optima in multimodal landscapes.

### Termination Criterion
- Define a maximum number of generations or function evaluations based on the available computational budget.
- Monitor the progress of the best solution found over generations. If no significant improvement is observed for a predefined number of generations, consider terminating the algorithm.
- Incorporate problem-specific knowledge, such as acceptable solution quality or convergence thresholds, to define appropriate stopping conditions.

### Constraint Handling
- For constrained optimization problems, modify the selection operator to compare solutions based on a constraint violation measure in addition to the objective function value.
- Apply penalty functions to penalize infeasible solutions and guide the search towards the feasible region.
- Employ repair mechanisms or specialized operators to handle constraints and maintain population feasibility.

