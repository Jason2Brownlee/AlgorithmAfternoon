# Novelty Search With Quality

## Name

Novelty Search with Quality (NS-Q)

## Taxonomy

Novelty Search with Quality is an extension of the Novelty Search algorithm that incorporates a quality measure to balance exploration and exploitation in stochastic optimization. It is closely related to Novelty Search and Quality Diversity algorithms.

- Computational Intelligence
  - Stochastic Optimization
    - Biologically Inspired Computation
      - Evolutionary Computation
        - Novelty Search
          - Novelty Search with Quality

## Strategy

Novelty Search with Quality combines the exploration capabilities of Novelty Search with a quality measure to ensure that the solutions discovered are not only novel but also of high quality. The algorithm maintains an archive of previously discovered solutions, which is used to compute the novelty of new solutions. The novelty measure encourages the exploration of uncharted areas of the search space, while the quality measure ensures that the solutions found are of practical value.

The algorithm starts by initializing a population of random solutions and evaluating their novelty and quality. In each iteration, a subset of solutions is selected based on their novelty and quality scores. These selected solutions are then used to generate new offspring through genetic operators such as mutation and crossover. The novelty and quality of the offspring are evaluated, and they are added to the population if they meet certain criteria.

The novelty of a solution is determined by its distance to the nearest neighbors in the archive. Solutions that are far from their nearest neighbors are considered more novel. The quality of a solution is measured using a domain-specific fitness function that assesses its performance on the given problem.

The algorithm maintains a balance between exploration and exploitation by adjusting the relative importance of novelty and quality during the search process. This is typically achieved by using a dynamic weighting scheme that adapts to the progress of the search.

## Procedure

Data Structures:
- Population: A set of candidate solutions
- Archive: A set of previously discovered solutions

Parameters:
- Population Size: The number of candidate solutions in the population
- Novelty Threshold: The minimum novelty required for a solution to be added to the archive
- Quality Threshold: The minimum quality required for a solution to be considered viable
- Novelty-Quality Balance: The relative importance of novelty and quality in the selection process

1. Initialize the population with random solutions
2. Evaluate the novelty and quality of each solution in the population
3. Add solutions that meet the novelty and quality thresholds to the archive
4. While the termination criteria are not met:
   1. Select a subset of solutions from the population based on their novelty and quality scores
   2. Generate offspring from the selected solutions using genetic operators
   3. Evaluate the novelty and quality of the offspring
   4. Add offspring that meet the novelty and quality thresholds to the archive
   5. Update the population by replacing low-novelty or low-quality solutions with the new offspring
   6. Adjust the novelty-quality balance based on the progress of the search
5. Return the best solution found

## Considerations

Advantages:
- Promotes the discovery of diverse and high-quality solutions
- Balances exploration and exploitation in the search process
- Adaptable to various problem domains through the use of domain-specific quality measures

Disadvantages:
- Requires the definition of a suitable novelty measure, which may be challenging for some problems
- The performance of the algorithm is sensitive to the choice of parameters, such as the novelty and quality thresholds
- May require a larger computational budget compared to traditional optimization algorithms due to the added complexity of novelty calculation

## Heuristics

Parameter Selection:
- The population size should be large enough to maintain diversity but not so large that it slows down the search process
- The novelty threshold should be set high enough to promote exploration but not so high that it prevents the discovery of viable solutions
- The quality threshold should be set based on the desired performance level for the given problem
- The novelty-quality balance should be adjusted dynamically based on the progress of the search, with more emphasis on novelty in the early stages and more emphasis on quality in the later stages

Novelty Measure:
- The novelty measure should be designed to capture the relevant features of the problem domain
- Consider using a combination of behavioral and genotypic distances to assess novelty
- Normalize the novelty scores to ensure a fair comparison between solutions

Quality Measure:
- The quality measure should be a good indicator of the solution's performance on the given problem
- Consider using a combination of multiple objectives or constraints to define quality
- Ensure that the quality measure is computationally efficient to evaluate

Genetic Operators:
- Use mutation operators that introduce sufficient variation to explore the search space effectively
- Consider using crossover operators that preserve the important features of the parent solutions
- Adapt the mutation and crossover rates based on the diversity of the population and the progress of the search

Population Management:
- Maintain a balance between high-novelty and high-quality solutions in the population
- Consider using a diversity maintenance mechanism, such as crowding or niching, to prevent premature convergence
- Remove low-novelty or low-quality solutions from the population to make room for new offspring


