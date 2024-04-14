# MAP-Elites

## Name

MAP-Elites, Multidimensional Archive of Phenotypic Elites

## Taxonomy

MAP-Elites is a quality diversity algorithm that belongs to the field of Evolutionary Computation, a subfield of Computational Intelligence. It is closely related to the Novelty Search algorithm and the Novelty Search with Local Competition (NSLC) algorithm.

- Artificial Intelligence
  - Computational Intelligence
    - Evolutionary Computation
      - Evolutionary Algorithms
        - Quality Diversity Algorithms
          - MAP-Elites

## Strategy

MAP-Elites maintains a grid of elite solutions, where each cell in the grid represents a unique combination of predefined feature dimensions. The algorithm starts by randomly generating an initial population of solutions and evaluating their performance and feature descriptors. Each solution is then placed into the corresponding cell in the grid based on its feature values. If the cell is empty or the new solution outperforms the existing one, it replaces the current occupant.

The algorithm proceeds by repeatedly selecting a cell from the grid, either uniformly at random or based on a biased selection strategy. A new solution is then created by applying genetic operators, such as mutation and/or crossover, to the selected solution. The new solution is evaluated and placed into the appropriate cell in the grid, potentially replacing an existing solution if it performs better.

This process continues for a predetermined number of iterations or until a satisfactory level of diversity and quality is achieved. The result is a grid of elite solutions that span the feature space, providing a diverse set of high-performing solutions.

### Niching and Diversity Maintenance

MAP-Elites promotes diversity by maintaining a collection of elite solutions in each cell of the feature grid. This niching strategy ensures that the algorithm explores and preserves solutions with unique combinations of features, preventing the population from converging to a single optimal solution.

### Quality and Performance Optimization

While MAP-Elites focuses on diversity, it also optimizes the quality of solutions within each cell of the feature grid. By replacing solutions with better-performing ones, the algorithm continuously improves the quality of the elite solutions in each niche.

## Procedure

Data Structures:
- `grid`: A multidimensional grid that stores elite solutions based on their feature descriptors.
- `solution`: An individual solution in the population, consisting of its genome, performance metric, and feature descriptors.

Parameters:
- `num_iterations`: The number of iterations to run the MAP-Elites algorithm.
- `population_size`: The initial population size.
- `feature_dimensions`: The number and definition of feature dimensions for the grid.
- `mutation_rate`: The probability of applying mutation to a solution.
- `crossover_rate`: The probability of applying crossover to a pair of solutions.

Steps:
1. Initialize an empty `grid` with dimensions based on `feature_dimensions`.
2. Generate an initial population of `population_size` random solutions.
3. Evaluate the performance and feature descriptors of each solution in the population.
4. For each solution in the population:
   - Determine the corresponding cell in the `grid` based on its feature descriptors.
   - If the cell is empty or the solution outperforms the existing one, place the solution in the cell.
5. Repeat for `num_iterations`:
   - Select a cell from the `grid`, either uniformly at random or using a biased selection strategy.
   - Create a new solution by applying genetic operators (mutation and/or crossover) to the selected solution.
   - Evaluate the performance and feature descriptors of the new solution.
   - Determine the corresponding cell in the `grid` based on the new solution's feature descriptors.
   - If the cell is empty or the new solution outperforms the existing one, place the new solution in the cell.
6. Return the `grid` containing the elite solutions.

## Considerations

Advantages:
- Maintains a diverse set of high-performing solutions across the feature space.
- Allows for the discovery of novel and unexpected solutions by exploring different niches.
- Provides a way to analyze the relationship between features and performance.

Disadvantages:
- The performance of MAP-Elites depends on the choice of feature dimensions, which may require domain knowledge.
- The size of the grid grows exponentially with the number of feature dimensions, leading to high computational costs and memory requirements.
- The algorithm may struggle to find high-quality solutions in sparse regions of the feature space.

## Heuristics

### Feature Dimension Selection
- Choose feature dimensions that are relevant to the problem domain and capture important aspects of the solutions.
- Consider using a low number of feature dimensions (e.g., 2-5) to keep the grid size manageable.
- Ensure that the feature dimensions are independent and provide meaningful diversity.

### Grid Resolution
- Determine the resolution of each feature dimension based on the desired granularity and computational resources available.
- Higher grid resolutions can capture more nuanced differences between solutions but increase the computational cost.
- Consider using adaptive or dynamic grid resolutions that change during the course of the algorithm.

### Genetic Operators
- Use mutation operators that introduce meaningful variations to the solutions while preserving their overall structure.
- Apply crossover operators that allow for the exchange of genetic material between solutions in different niches.
- Adjust the mutation and crossover rates based on the desired balance between exploration and exploitation.

### Selection Strategy
- Experiment with different selection strategies, such as uniform random selection, biased selection based on cell quality, or curiosity-driven selection.
- Consider using a combination of selection strategies to balance exploration and exploitation.

### Initialization and Restarts
- Initialize the population with a diverse set of random solutions to encourage exploration of the feature space.
- Periodically reset or partially randomize the grid to escape local optima and discover new promising regions.

### Performance Evaluation
- Define a performance metric that accurately captures the desired behavior or quality of the solutions.
- Consider using multiple performance metrics to assess different aspects of the solutions and promote diversity.

### Parallelization and Distributed Computing
- Leverage parallel computing techniques to evaluate and update the grid cells concurrently, improving efficiency.
- Explore distributed computing approaches to scale MAP-Elites to larger problem sizes and higher-dimensional feature spaces.
