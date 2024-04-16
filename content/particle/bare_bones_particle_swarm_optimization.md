# Bare Bones Particle Swarm Optimization

## Name

Bare Bones Particle Swarm Optimization (BBPSO), Simplified PSO, Basic PSO

## Taxonomy

Bare Bones Particle Swarm Optimization is a simplification of the standard Particle Swarm Optimization algorithm, which belongs to the field of Swarm Intelligence, a subfield of Computational Intelligence and Biologically Inspired Computation. It is closely related to other swarm-based optimization algorithms such as Ant Colony Optimization and Bee Colony Optimization.

- Computational Intelligence
  - Biologically Inspired Computation
    - Swarm Intelligence
      - Particle Swarm Optimization (PSO)
        - Bare Bones Particle Swarm Optimization (BBPSO)

## Strategy

### Gaussian Distribution Sampling

In contrast to the standard PSO, which updates particle positions using velocity vectors, BBPSO simplifies the position update process by sampling from a Gaussian distribution. The mean of this distribution is calculated as the average of the particle's personal best position and the global best position, while the standard deviation is the absolute difference between these two positions.

### Exploration and Exploitation Balance

By sampling from a Gaussian distribution, BBPSO inherently balances exploration and exploitation. When the personal best and global best positions are far apart, the standard deviation is large, encouraging exploration of the search space. As the algorithm converges and these positions move closer together, the standard deviation decreases, focusing the search around promising areas.

### Simplified Update Process

The use of Gaussian sampling eliminates the need for velocity updates and associated parameters such as inertia weight and acceleration coefficients. This simplification reduces the computational complexity of the algorithm and the number of parameters that need to be tuned.

## Procedure

### Data Structures

- Particle: Represents a candidate solution, consisting of a position vector and a personal best position vector.
- Swarm: A collection of particles, representing the population of candidate solutions.

### Parameters

- `num_particles`: The number of particles in the swarm.
- `num_dimensions`: The dimensionality of the search space.
- `max_iterations`: The maximum number of iterations allowed for the algorithm to run.

### Steps

1. Initialize the swarm:
   1. For each particle in the swarm:
      1. Randomly initialize the particle's position within the search space bounds.
      2. Set the particle's personal best position to its initial position.
   2. Set the global best position to the best personal best position among all particles.

2. Repeat until termination criteria are met (e.g., maximum iterations reached or satisfactory solution found):
   1. For each particle in the swarm:
      1. Update the particle's position:
         1. Calculate the mean of the particle's personal best position and the global best position.
         2. Calculate the standard deviation as the absolute difference between the personal best and global best positions.
         3. Sample a new position from a Gaussian distribution with the calculated mean and standard deviation.
      2. Evaluate the fitness of the particle's new position.
      3. If the new position has a better fitness than the particle's personal best position, update the personal best position.
   2. Update the global best position if any particle has found a better solution.

3. Return the global best position as the best solution found.

## Considerations

### Advantages

- Simplicity: BBPSO has a simpler update process compared to standard PSO, making it easier to understand and implement.
- Fewer parameters: The elimination of velocity updates and associated parameters reduces the number of parameters that need to be tuned.
- Balanced exploration and exploitation: The Gaussian sampling approach inherently balances exploration and exploitation based on the convergence state of the algorithm.

### Disadvantages

- Limited control: The simplified update process reduces the level of control over the balance between exploration and exploitation compared to standard PSO.
- Lack of momentum: The absence of a velocity component may result in slower convergence in some cases, as particles do not maintain a "momentum" in a particular direction.
- Potential premature convergence: If the global best position is located in a suboptimal region, the algorithm may converge prematurely, as particles are strongly influenced by the global best.

## Heuristics

### Swarm Size

- Start with a swarm size of around 20-50 particles for most problems.
- Increase the swarm size for high-dimensional problems or those with many local optima.
- Decrease the swarm size for simpler problems to reduce computational cost.

### Initialization

- Initialize particles randomly within the search space bounds to ensure good coverage.
- If prior knowledge about the problem is available, consider initializing particles in promising regions.

### Termination Criteria

- Set a maximum number of iterations based on the problem complexity and available computational resources.
- Use a tolerance threshold for the change in the global best fitness to detect convergence.
- Implement a time limit to bound the algorithm's runtime.

### Constraint Handling

- For constrained optimization problems, apply a penalty function to the fitness evaluation to discourage infeasible solutions.
- Alternatively, use a repair mechanism to ensure that particle positions remain within the feasible region.

### Hybrid Approaches

- Consider combining BBPSO with local search techniques to refine solutions in promising regions.
- Incorporate problem-specific heuristics or operators to improve the algorithm's effectiveness for a particular domain.
