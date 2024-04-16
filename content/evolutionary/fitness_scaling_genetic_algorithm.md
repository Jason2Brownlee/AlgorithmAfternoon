# Fitness Scaling Genetic Algorithm

## Name

Fitness Scaling Genetic Algorithm, Fitness Scaling GA, FSGA

## Taxonomy

Fitness Scaling Genetic Algorithm is a variation of the standard Genetic Algorithm, which belongs to the field of Evolutionary Computation, a subfield of Computational Intelligence and Biologically Inspired Computation. It is closely related to other GA variations such as Rank Selection GA and Boltzmann Selection GA.

- Computational Intelligence
  - Biologically Inspired Computation
    - Evolutionary Computation
      - Evolutionary Algorithms
        - Genetic Algorithms
          - Fitness Scaling Genetic Algorithm

## Strategy

The Fitness Scaling Genetic Algorithm introduces a fitness scaling mechanism to the standard GA to mitigate the effects of dominant individuals in the population, which can lead to premature convergence. By scaling the fitness values of individuals, the selection pressure can be controlled, allowing for a more balanced exploration and exploitation of the search space.

### Fitness Scaling

The raw fitness values of individuals are transformed using a scaling function. Common scaling methods include linear scaling, sigma truncation, and power law scaling. The choice of scaling function depends on the problem characteristics and the desired selection pressure.

### Selection

After fitness scaling, the standard GA selection methods, such as roulette wheel selection or tournament selection, are applied to the scaled fitness values. This ensures that the selection probability of an individual is proportional to its relative scaled fitness rather than its raw fitness.

### Genetic Operators

The standard GA genetic operators, namely crossover and mutation, are applied to the selected individuals to create the next generation. The scaled fitness values do not directly affect the genetic operators, but rather influence the selection process that determines which individuals participate in reproduction.

## Procedure

Data Structures:
- Population: An array of individuals representing potential solutions to the problem.
- Individual: Represents a single solution, typically encoded as a binary string or a real-valued vector.
- Fitness: An array storing the fitness value of each individual in the population.
- Scaled Fitness: An array storing the scaled fitness value of each individual in the population.

Parameters:
- Population Size: The number of individuals in the population.
- Crossover Rate: The probability of applying the crossover operator to a pair of selected individuals.
- Mutation Rate: The probability of applying the mutation operator to an individual.
- Scaling Method: The fitness scaling function to be used (e.g., linear scaling, sigma truncation, power law scaling).
- Scaling Parameters: Additional parameters specific to the chosen scaling method (e.g., scaling factor, truncation threshold).

1. Initialize the population
   1. Create an array of individuals with random genetic information
   2. Evaluate the fitness of each individual in the population
   3. Store the fitness values in the Fitness array

2. While termination criteria are not met, repeat steps 3-7

3. Scale the fitness values
   1. Apply the chosen scaling method to the Fitness array
   2. Store the scaled fitness values in the Scaled Fitness array

4. Select individuals for reproduction
   1. Use a selection method (e.g., roulette wheel, tournament) based on the Scaled Fitness array
   2. Select pairs of individuals to create the mating pool

5. Apply the crossover operator
   1. For each pair of selected individuals, generate a random number between 0 and 1
   2. If the random number is less than the Crossover Rate, apply crossover to create offspring
   3. Otherwise, add the selected individuals to the new population without modification

6. Apply the mutation operator
   1. For each individual in the new population, generate a random number between 0 and 1
   2. If the random number is less than the Mutation Rate, apply mutation to the individual

7. Replace the old population with the new population
   1. Evaluate the fitness of each individual in the new population
   2. Store the fitness values in the Fitness array

8. Return the best solution found

## Considerations

Advantages:
- Helps prevent premature convergence by controlling the selection pressure
- Allows for a better balance between exploration and exploitation of the search space
- Can handle problems with large differences in fitness values among individuals

Disadvantages:
- Introduces additional parameters (scaling method and its associated parameters) that need to be tuned
- The choice of scaling method may depend on the problem characteristics, requiring experimentation
- Fitness scaling adds computational overhead compared to the standard GA

## Heuristics

### Choosing a Scaling Method

- Linear scaling is simple and effective for problems with a narrow range of fitness values
- Sigma truncation is suitable when the population has a few extremely fit individuals that need to be controlled
- Power law scaling can provide a adjustable balance between exploration and exploitation by varying the scaling factor

### Setting the Scaling Parameters

- For linear scaling, the scaling factor should be chosen to maintain a reasonable selection pressure without causing premature convergence
- In sigma truncation, the truncation threshold should be set based on the desired level of selection pressure and the fitness distribution of the population
- For power law scaling, the scaling factor should be adjusted based on the problem characteristics and the desired balance between exploration and exploitation

### Balancing Selection Pressure

- Start with a low selection pressure (e.g., linear scaling with a small scaling factor) to encourage exploration in the early generations
- Gradually increase the selection pressure over the course of the run to shift the focus towards exploitation and convergence
- Monitor the population diversity and adjust the scaling parameters if premature convergence is observed

### Combining with Other GA Variations

- Fitness scaling can be combined with other GA variations, such as niching methods or adaptive operators, to further improve performance
- When combining techniques, be cautious of the increased complexity and the potential for unexpected interactions between the different components
- Experiment with different combinations and parameter settings to find the most effective configuration for the problem at hand

