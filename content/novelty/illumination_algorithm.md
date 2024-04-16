# Illumination Algorithm

## Name

Illumination Algorithm, Illumination Approach

## Taxonomy

The Illumination Algorithm is a metaheuristic optimization technique inspired by the concept of illumination in optics and physics. It shares similarities with other population-based metaheuristics such as Particle Swarm Optimization and Differential Evolution.

- Computational Intelligence
  - Stochastic Optimization
    - Biologically Inspired Computation
      - Swarm Intelligence
        - Particle Swarm Optimization
        - Ant Colony Optimization
      - Evolutionary Computation
        - Genetic Algorithms
        - Differential Evolution
    - Physics-Inspired Computation
      - Illumination Algorithm
      - Simulated Annealing
      - Gravitational Search Algorithm

## Strategy

The Illumination Algorithm operates by maintaining a population of candidate solutions, referred to as "light points," which explore the search space guided by the principles of light propagation and interaction. Each light point is characterized by its position in the search space and an associated intensity value that represents its fitness or quality.

The algorithm iteratively updates the positions and intensities of the light points based on their interactions with each other and the environment. The movement of light points is influenced by the concept of refraction, where light points are attracted towards regions of higher fitness (higher refractive index) and repelled from regions of lower fitness (lower refractive index).

Additionally, the algorithm incorporates the notion of reflection, where light points can bounce off constraints or boundaries in the search space, allowing them to explore new regions and maintain feasibility. The intensity of each light point is adjusted based on its fitness value, with higher fitness resulting in higher intensity.

The Illumination Algorithm also introduces the concept of absorption, where light points with low intensity are absorbed by the environment, effectively eliminating them from the population. This mechanism helps maintain a focus on promising regions of the search space and promotes the convergence of the algorithm.

## Procedure

Data Structures:
- Population: An array of light points, where each light point is represented by its position and intensity.
- Best Solution: Stores the position and fitness value of the best solution found so far.

Parameters:
- Population Size: The number of light points in the population.
- Max Iterations: The maximum number of iterations allowed for the algorithm.
- Absorption Coefficient: Controls the rate at which low-intensity light points are absorbed.
- Refraction Coefficient: Determines the strength of attraction towards high-fitness regions.
- Reflection Coefficient: Controls the behavior of light points when they encounter constraints or boundaries.

Procedure:
1. Initialize the population of light points randomly within the search space.
2. Evaluate the fitness of each light point based on the objective function.
3. Update the Best Solution if a light point with better fitness is found.
4. Repeat steps 5-9 until the Max Iterations are reached or a termination criterion is met.
5. For each light point in the population:
   1. Calculate the refraction vector based on the fitness values of neighboring light points and the Refraction Coefficient.
   2. Update the position of the light point by moving it along the refraction vector.
   3. If the light point violates any constraints or boundaries, apply reflection by adjusting its position based on the Reflection Coefficient.
   4. Evaluate the fitness of the updated light point.
   5. Update the intensity of the light point based on its fitness value.
6. For each light point in the population:
   1. If the intensity of the light point falls below a threshold determined by the Absorption Coefficient, remove it from the population.
7. If the population size falls below a minimum threshold, create new random light points to maintain diversity.
8. Update the Best Solution if a light point with better fitness is found.
9. Return the Best Solution found.

## Considerations

Advantages:
- The Illumination Algorithm can effectively explore and exploit the search space, balancing local and global search.
- The concept of refraction allows the algorithm to be attracted towards promising regions of the search space.
- The reflection mechanism helps the algorithm handle constraints and maintain feasibility of solutions.

Disadvantages:
- The performance of the Illumination Algorithm depends on the proper tuning of its parameters, which may require experimentation.
- The algorithm may be sensitive to the initial population and can converge prematurely if not properly initialized.
- The computational complexity of the algorithm increases with the population size and the dimensionality of the problem.

## Heuristics

Population Size:
- The population size should be chosen based on the complexity and dimensionality of the problem.
- A larger population size can improve exploration but increases computational overhead.
- Typical values range from 20 to 100 light points, depending on the problem.

Absorption Coefficient:
- The absorption coefficient controls the elimination of low-intensity light points.
- A higher value leads to more aggressive absorption, promoting faster convergence but potentially missing good solutions.
- A lower value allows for more exploration but may slow down convergence.
- Typical values range from 0.01 to 0.1.

Refraction Coefficient:
- The refraction coefficient determines the strength of attraction towards high-fitness regions.
- A higher value leads to stronger attraction, encouraging exploitation of promising areas.
- A lower value allows for more exploration and can help escape local optima.
- Typical values range from 0.5 to 2.0.

Reflection Coefficient:
- The reflection coefficient controls the behavior of light points when they encounter constraints or boundaries.
- A value of 1.0 corresponds to perfect reflection, where the light point bounces back symmetrically.
- Values less than 1.0 result in dampened reflection, reducing the step size after reflection.
- Values greater than 1.0 can cause the light point to overshoot the boundary after reflection.
- Typical values range from 0.5 to 1.0.

Max Iterations:
- The maximum number of iterations should be set based on the available computational resources and the desired solution quality.
- A higher value allows for more thorough exploration and refinement of solutions but increases the computational cost.
- The max iterations can be adjusted dynamically based on the progress of the algorithm or the urgency of obtaining a solution.

