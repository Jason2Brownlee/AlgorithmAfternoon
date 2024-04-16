# Extended Compact Genetic Algorithm

## Name
Extended Compact Genetic Algorithm (eCGA)

## Taxonomy
The Extended Compact Genetic Algorithm is a probabilistic model-building genetic algorithm that belongs to the field of Evolutionary Computation, a subfield of Computational Intelligence. It is closely related to the Compact Genetic Algorithm (cGA) and the Bayesian Optimization Algorithm (BOA).

- Computational Intelligence
  - Evolutionary Computation
    - Evolutionary Algorithms
      - Genetic Algorithms
        - Probabilistic Model-Building Genetic Algorithms
          - Extended Compact Genetic Algorithm (eCGA)

## Strategy
The Extended Compact Genetic Algorithm is a probabilistic model-building genetic algorithm that aims to identify and exploit problem structure to efficiently solve optimization problems. It maintains a probabilistic model of promising solutions, which is used to generate new candidate solutions.

### Probabilistic Modeling
eCGA represents the population as a probability distribution over the search space. The probabilistic model captures the dependencies between problem variables, allowing the algorithm to exploit problem structure and generate high-quality solutions.

### Model Building and Sampling
In each generation, eCGA builds a probabilistic model based on a selected set of promising solutions. The model is typically a marginal product model, which assumes that the problem variables can be partitioned into subsets, each following a separate probability distribution. New candidate solutions are then sampled from this model.

### Selection and Model Updating
After evaluating the sampled solutions, eCGA selects the most promising ones based on their fitness values. These selected solutions are then used to update the probabilistic model, refining the search direction for the next generation.

## Procedure
Data Structures:
- Probabilistic Model: A data structure representing the probability distribution over the search space, typically a marginal product model.
- Population: A set of candidate solutions.

Parameters:
- Population Size: The number of candidate solutions maintained in each generation.
- Selection Pressure: The proportion of the population selected for model building and updating.
- Learning Rate: The rate at which the probabilistic model is updated based on the selected solutions.

1. Initialize the probabilistic model
   1.1. Set initial probabilities for each problem variable
2. Generate an initial population by sampling from the probabilistic model
3. Evaluate the fitness of each candidate solution in the population
4. While the termination criterion is not met, repeat:
   4.1. Select a set of promising solutions from the population based on their fitness
   4.2. Build a new probabilistic model based on the selected solutions
   4.3. Sample a new population from the updated probabilistic model
   4.4. Evaluate the fitness of each new candidate solution
   4.5. Replace the old population with the new population
5. Return the best solution found

## Considerations
Advantages:
- Exploits problem structure by capturing dependencies between variables
- Requires fewer evaluations compared to traditional genetic algorithms
- Suitable for problems with large search spaces and complex variable interactions

Disadvantages:
- The performance depends on the choice of the probabilistic model
- Building the probabilistic model can be computationally expensive
- May prematurely converge to suboptimal solutions if the model is not expressive enough

## Heuristics
### Population Size
- Start with a population size that is at least 10 times the problem size (number of variables)
- Increase the population size for problems with complex variable interactions or large search spaces

### Selection Pressure
- Use a moderate selection pressure (e.g., 50% of the population) to balance exploration and exploitation
- Higher selection pressure can lead to faster convergence but may result in premature convergence to suboptimal solutions

### Learning Rate
- Set the learning rate to a small value (e.g., 0.1) to avoid rapid changes in the probabilistic model
- Gradually increase the learning rate over generations to refine the search direction

### Probabilistic Model
- Use a marginal product model as the default choice for the probabilistic model
- Consider more expressive models, such as Bayesian networks, for problems with complex variable interactions
- Adapt the model complexity based on the problem size and available computational resources

### Termination Criterion
- Set a maximum number of generations or fitness evaluations based on the available computational budget
- Terminate the algorithm if the best solution's fitness has not improved for a specified number of generations
- Consider problem-specific termination criteria, such as reaching a target fitness value or solution quality