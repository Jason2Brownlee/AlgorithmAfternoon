# Messy Genetic Algorithm

## Name

Messy Genetic Algorithm (Messy GA)

## Taxonomy

Messy Genetic Algorithm is a variant of the Genetic Algorithm, a population-based optimization technique inspired by the principles of natural selection and genetic evolution, belonging to the field of Evolutionary Computation, a subfield of Computational Intelligence.

- Computational Intelligence
  - Biologically Inspired Computation
    - Evolutionary Computation
      - Evolutionary Algorithms
        - Genetic Algorithms
          - Messy Genetic Algorithm

## Strategy

The Messy Genetic Algorithm is designed to address the limitations of the traditional Genetic Algorithm in handling problems with variable-length representations and non-coding segments. It introduces the concept of messy chromosomes, which are variable-length strings that can contain both coding and non-coding regions, allowing for greater flexibility in problem representation.

The algorithm operates in two phases: the primordial phase and the juxtapositional phase. In the primordial phase, a large population of messy chromosomes is generated, containing a diverse set of building blocks or partial solutions. These messy chromosomes undergo a selection process based on their fitness, with the fittest individuals being chosen for reproduction.

During the juxtapositional phase, the selected messy chromosomes are subjected to genetic operators such as cut and splice, which allow for the recombination of building blocks from different individuals. The cut operator randomly divides a messy chromosome into two parts, while the splice operator concatenates two messy chromosomes to create a new offspring. This process of recombination and selection is repeated for a specified number of generations or until a satisfactory solution is found.

The Messy Genetic Algorithm incorporates mechanisms to maintain diversity in the population and prevent premature convergence. It allows for the exploration of a wider range of potential solutions by considering variable-length representations and the presence of non-coding regions, which can contribute to the overall fitness of the individuals.

## Procedure

Data Structures:
- Population: A collection of messy chromosomes representing potential solutions.
- Messy Chromosome: A variable-length string that can contain both coding and non-coding regions.

Parameters:
- Population Size: The number of messy chromosomes in the population.
- Primordial Phase Length: The number of generations in the primordial phase.
- Juxtapositional Phase Length: The number of generations in the juxtapositional phase.
- Cut Probability: The probability of applying the cut operator to a messy chromosome.
- Splice Probability: The probability of applying the splice operator to two messy chromosomes.

Steps:
1. Initialization:
   1. Generate an initial population of messy chromosomes with variable lengths and random compositions of coding and non-coding regions.
   2. Evaluate the fitness of each messy chromosome based on the problem-specific objective function.

2. Primordial Phase:
   1. Repeat for the specified number of primordial phase generations:
      1. Select a subset of the fittest messy chromosomes from the population based on their fitness values.
      2. Apply the cut operator to the selected messy chromosomes based on the cut probability.
      3. Apply the splice operator to the selected messy chromosomes based on the splice probability.
      4. Evaluate the fitness of the newly created messy chromosomes.
      5. Replace the least fit messy chromosomes in the population with the newly created ones.

3. Juxtapositional Phase:
   1. Repeat for the specified number of juxtapositional phase generations:
      1. Select a subset of the fittest messy chromosomes from the population based on their fitness values.
      2. Apply the cut operator to the selected messy chromosomes based on the cut probability.
      3. Apply the splice operator to the selected messy chromosomes based on the splice probability.
      4. Evaluate the fitness of the newly created messy chromosomes.
      5. Replace the least fit messy chromosomes in the population with the newly created ones.

4. Termination:
   1. Check if the termination criteria are met (e.g., maximum number of generations, satisfactory solution found).
   2. If the termination criteria are not met, go back to step 3.
   3. If the termination criteria are met, return the best messy chromosome found as the solution.

## Considerations

Advantages:
- Handles variable-length representations and non-coding regions, allowing for greater flexibility in problem representation.
- Explores a wider range of potential solutions by considering diverse building blocks in the primordial phase.
- Promotes the recombination of promising building blocks through the cut and splice operators in the juxtapositional phase.

Disadvantages:
- Increased complexity compared to the traditional Genetic Algorithm due to the variable-length representations and additional operators.
- May require careful tuning of parameters, such as the cut and splice probabilities, to achieve optimal performance.
- The presence of non-coding regions can introduce additional overhead and may slow down the convergence process.

## Heuristics

### Population Size
- Start with a relatively large population size in the primordial phase to ensure a diverse set of building blocks.
- Reduce the population size in the juxtapositional phase to focus on the recombination of promising building blocks.
- Adjust the population size based on the complexity of the problem and available computational resources.

### Primordial Phase Length
- Set the primordial phase length to allow sufficient generations for the exploration of diverse building blocks.
- Consider the problem complexity and the desired level of exploration when determining the primordial phase length.
- Monitor the convergence behavior and adjust the primordial phase length accordingly.

### Juxtapositional Phase Length
- Set the juxtapositional phase length to provide enough generations for the recombination and refinement of building blocks.
- Consider the problem complexity and the desired level of exploitation when determining the juxtapositional phase length.
- Monitor the convergence behavior and adjust the juxtapositional phase length accordingly.

### Cut and Splice Probabilities
- Start with moderate cut and splice probabilities to balance exploration and exploitation.
- Adjust the cut probability to control the frequency of dividing messy chromosomes into smaller building blocks.
- Adjust the splice probability to control the frequency of combining building blocks from different messy chromosomes.
- Experiment with different values and observe the impact on the algorithm's performance.

### Fitness Evaluation
- Design a fitness function that accurately captures the quality of messy chromosomes in relation to the problem objectives.
- Consider both the coding and non-coding regions when evaluating fitness, as non-coding regions may contribute to the overall solution quality.
- Ensure that the fitness function is computationally efficient, especially for large populations and complex problems.

### Diversity Maintenance
- Incorporate mechanisms to maintain diversity in the population, such as niching or crowding techniques.
- Consider introducing random mutations or immigrations to inject new genetic material and prevent premature convergence.
- Monitor the diversity of the population and take appropriate actions if diversity drops below a certain threshold.

