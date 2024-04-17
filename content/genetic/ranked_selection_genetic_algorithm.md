# Ranked Selection Genetic Algorithm

## Name

Ranked Selection Genetic Algorithm, Rank Selection, Rank-based Selection

## Taxonomy

Ranked Selection Genetic Algorithm is a variation of the Genetic Algorithm, a popular optimization technique inspired by the principles of natural selection and evolution, belonging to the field of Evolutionary Computation, a subfield of Computational Intelligence. It is closely related to other selection methods such as Tournament Selection and Fitness Proportionate Selection.

- Computational Intelligence
  - Evolutionary Computation
    - Evolutionary Algorithms
      - Genetic Algorithms
        - Selection Methods
          - Ranked Selection Genetic Algorithm

## Strategy

The Ranked Selection Genetic Algorithm introduces a different approach to the selection phase of the standard Genetic Algorithm. Instead of directly using the fitness values to determine the selection probabilities, the individuals in the population are first sorted based on their fitness values, and then ranks are assigned to each individual. The selection probabilities are then calculated based on these ranks rather than the actual fitness values.

This ranking-based approach helps to mitigate the problems associated with direct fitness-based selection, such as premature convergence and the dominance of a few highly fit individuals in the early stages of the optimization process. By assigning ranks and using them for selection, the Ranked Selection Genetic Algorithm provides a more balanced and controlled selection pressure, allowing for better exploration of the search space and maintaining diversity in the population.

The ranks are typically assigned in a linear or exponential manner, with the best individual receiving the highest rank and the worst individual receiving the lowest rank. The selection probabilities are then calculated based on these ranks using a predefined formula or mapping function. This mapping function can be adjusted to control the selection pressure, with higher pressure favoring the top-ranked individuals and lower pressure providing a more even distribution of selection probabilities.

## Procedure

Data Structures:
- Population: A list or array of individuals representing potential solutions to the optimization problem.
- Individual: A single solution in the population, typically represented as a list or array of values (genes).
- Fitness Function: A function that evaluates the quality or fitness of an individual solution.

Parameters:
- Population Size: The number of individuals in the population.
- Mutation Rate: The probability of a gene being mutated during the mutation step.
- Crossover Rate: The probability of two individuals being selected for crossover.
- Selection Pressure: A parameter that controls the mapping of ranks to selection probabilities.

Steps:
1. Initialize the population with random individuals.
2. Evaluate the fitness of each individual in the population using the fitness function.
3. Sort the population based on the fitness values in descending order (best to worst).
4. Assign ranks to each individual based on their position in the sorted population.
5. Calculate the selection probabilities for each individual based on their rank using a predefined mapping function.
6. Repeat the following steps until a new population is generated:
   1. Select two parent individuals from the population using the calculated selection probabilities.
   2. Apply crossover to the selected parents to create offspring individuals.
   3. Apply mutation to the offspring individuals with a certain probability.
   4. Add the offspring individuals to the new population.
7. Replace the old population with the new population.
8. Repeat steps 2-7 until a termination criterion is met (e.g., maximum number of generations or desired fitness level).
9. Return the best individual found in the population as the solution.

## Considerations

Advantages:
- Reduced risk of premature convergence: By using ranks instead of direct fitness values, the Ranked Selection Genetic Algorithm mitigates the problem of a few highly fit individuals dominating the selection process in the early stages, allowing for better exploration of the search space.
- Maintains diversity: The ranking-based approach helps to maintain diversity in the population by providing a more balanced selection pressure, preventing the loss of potentially valuable genetic material.
- Adjustable selection pressure: The selection pressure can be easily adjusted by modifying the mapping function that translates ranks to selection probabilities, allowing for fine-tuning of the algorithm's behavior.

Disadvantages:
- Increased computational complexity: The Ranked Selection Genetic Algorithm requires sorting the population based on fitness values in each generation, which can be computationally expensive, especially for large populations.
- Sensitivity to ranking scheme: The performance of the algorithm can be sensitive to the choice of ranking scheme (linear, exponential, etc.) and the selection pressure parameter, requiring careful tuning for optimal results.
- Lack of fitness-proportionate selection: Unlike Fitness Proportionate Selection, the Ranked Selection Genetic Algorithm does not directly use the fitness values for selection, which may not be suitable for certain problems where the relative differences in fitness values are important.

## Heuristics

Population Size:
- Start with a population size that is large enough to maintain diversity and explore the search space effectively, typically in the range of 50-200 individuals.
- Increase the population size for more complex problems or larger search spaces to ensure adequate coverage and diversity.

Mutation Rate:
- Set the mutation rate low enough to avoid disrupting good solutions too frequently, typically in the range of 0.01-0.1.
- Adjust the mutation rate based on the problem complexity and the desired level of exploration. Higher mutation rates can be beneficial for problems with many local optima.

Crossover Rate:
- Set the crossover rate high enough to promote the exchange of genetic material between individuals, typically in the range of 0.6-0.9.
- Experiment with different crossover rates to find a balance between exploration and exploitation.

Selection Pressure:
- Start with a moderate selection pressure that provides a balance between favoring high-ranking individuals and maintaining diversity.
- Increase the selection pressure if the algorithm is not converging fast enough or if you want to focus more on exploitation of good solutions.
- Decrease the selection pressure if the algorithm is converging prematurely or if you want to encourage more exploration of the search space.

Ranking Scheme:
- Use a linear ranking scheme as a starting point, where the selection probability decreases linearly from the best to the worst individual.
- Consider using an exponential ranking scheme if you want to put more emphasis on the top-ranked individuals and create a stronger selection pressure.
- Experiment with different ranking schemes and observe their impact on the algorithm's performance for your specific problem.

Termination Criteria:
- Set a maximum number of generations as a termination criterion to prevent the algorithm from running indefinitely.
- Consider using a fitness-based termination criterion, where the algorithm stops if the best fitness value reaches a certain threshold or if there is no improvement in the best fitness for a specified number of generations.
- Monitor the convergence of the population and stop the algorithm if the diversity falls below a certain level to avoid wasting computational resources on an converged population.
