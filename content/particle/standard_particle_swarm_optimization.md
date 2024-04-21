# Standard Particle Swarm Optimization

## Name

Particle Swarm Optimization (PSO), Particle Swarm Algorithm, Swarm Intelligence Optimization, Swarm Optimization

## Taxonomy

Particle Swarm Optimization is a population-based stochastic optimization technique inspired by the social behavior of flocking birds or schooling fish, belonging to the field of Swarm Intelligence, which is a subfield of Computational Intelligence and Biologically Inspired Computation. It is closely related to other swarm intelligence algorithms like Ant Colony Optimization (ACO) and Artificial Bee Colony (ABC) optimization.

- Computational Intelligence
  - Biologically Inspired Computation
    - Swarm Intelligence
      - Particle Swarm Optimization (PSO)
      - Ant Colony Optimization (ACO)
      - Artificial Bee Colony (ABC) Optimization

## Strategy

Particle Swarm Optimization is based on the idea of simulating the social behavior of animals that live in groups, such as birds in a flock or fish in a school. The algorithm maintains a population of candidate solutions, called particles, which move through the search space based on their own experience and the experience of the swarm as a whole.

### Particle Movement

Each particle in the swarm has a position and a velocity. The position represents a candidate solution to the optimization problem, while the velocity determines the direction and magnitude of the particle's movement in the search space. Particles adjust their velocities based on their own best-known position (personal best) and the best-known position of the entire swarm (global best). This allows particles to learn from their own experiences and the experiences of others in the swarm.

### Swarm Interaction

Particles in the swarm communicate with each other by sharing information about their best-known positions. This social interaction allows the swarm to collectively explore the search space and converge towards promising regions. The global best position acts as an attractor, guiding the particles towards the most promising solutions found by the swarm.

### Iterative Optimization

The optimization process in PSO is iterative. At each iteration, particles update their velocities and positions based on their personal best and the global best. The velocity update equation balances the influence of the particle's own experience (cognitive component) and the experience of the swarm (social component). The position update equation then applies the updated velocity to the particle's current position, moving it to a new location in the search space.

### Convergence and Termination

As the iterations progress, particles converge towards the best solutions found by the swarm. The algorithm terminates when a specified stopping criterion is met, such as reaching a maximum number of iterations or finding a solution of sufficient quality. The global best position at the end of the optimization process represents the best solution found by the swarm.

## Procedure

### Data Structures

- Particle: Represents a candidate solution in the search space, consisting of a position vector and a velocity vector.
- Swarm: A collection of particles that interact and collaborate to find the optimal solution.

### Parameters

- Population Size: The number of particles in the swarm.
- Inertia Weight: A parameter that controls the influence of a particle's previous velocity on its current velocity.
- Cognitive Coefficient: A parameter that determines the influence of a particle's personal best position on its velocity.
- Social Coefficient: A parameter that determines the influence of the swarm's global best position on a particle's velocity.
- Maximum Velocity: A parameter that limits the maximum velocity of particles to prevent them from overshooting the search space.

### Pseudocode

1. Initialize the swarm
   1. For each particle in the swarm:
      1. Initialize the particle's position randomly within the search space
      2. Initialize the particle's velocity randomly
      3. Set the particle's personal best position to its initial position
   2. Set the global best position to the best position among all particles

2. Repeat until termination criteria are met:
   1. For each particle in the swarm:
      1. Update the particle's velocity based on its personal best and the global best
      2. Update the particle's position by applying the updated velocity
      3. Evaluate the fitness of the particle's new position
      4. If the new position is better than the particle's personal best:
         1. Update the particle's personal best position
         2. If the new position is better than the global best:
            1. Update the global best position
   2. Check termination criteria (e.g., maximum iterations, desired solution quality)

3. Return the global best position as the optimal solution

## Considerations

### Advantages

- Simplicity: PSO is relatively simple to implement and has few parameters to tune, making it easy to apply to a wide range of optimization problems.
- Fast Convergence: PSO often converges quickly towards good solutions, especially in problems with continuous search spaces.
- Adaptability: PSO can adapt to changing environments and can be easily modified to incorporate problem-specific knowledge or constraints.

### Disadvantages

- Premature Convergence: PSO may converge prematurely to suboptimal solutions, especially in complex multimodal problems.
- Lack of Diversity: As particles converge towards the global best, the swarm may lose diversity, limiting its ability to explore the search space effectively.
- Parameter Sensitivity: The performance of PSO can be sensitive to the choice of parameters, such as the inertia weight and cognitive/social coefficients, requiring careful tuning for specific problems.

## Heuristics

### Population Size

- Start with a population size of around 20-50 particles and adjust based on the problem complexity and available computational resources.
- Larger populations may be beneficial for complex multimodal problems to maintain diversity and avoid premature convergence.

### Inertia Weight

- Use an inertia weight that balances exploration and exploitation, typically in the range of 0.4 to 0.9.
- Higher inertia weights promote exploration, while lower values encourage exploitation of promising regions.
- Consider using adaptive inertia weights that decrease over time to transition from exploration to exploitation.

### Cognitive and Social Coefficients

- Set the cognitive and social coefficients to values around 2.0, which has been found to work well in many problems.
- Adjust the balance between the cognitive and social components based on the problem characteristics. Higher cognitive coefficients encourage individual exploration, while higher social coefficients promote swarm collaboration.

### Maximum Velocity

- Limit the maximum velocity of particles to a fraction of the search space range (e.g., 10-20%) to prevent particles from overshooting the optimal solution.
- Adjust the maximum velocity based on the problem scale and the desired balance between exploration and exploitation.

### Termination Criteria

- Define a maximum number of iterations based on the problem complexity and available computational resources.
- Consider using additional termination criteria, such as detecting convergence (e.g., small improvements over a specified number of iterations) or reaching a desired solution quality.

### Problem-Specific Modifications

- Incorporate problem-specific knowledge or constraints into the particle representation, velocity update, or position update equations.
- Use specialized initialization techniques, such as opposition-based learning or quasi-random sequences, to improve the initial swarm diversity.
- Apply local search techniques, such as hill climbing or simulated annealing, to refine the solutions found by PSO and overcome local optima.

## Code

{{< details "Show" >}}

### Python Particle Swarm Optimization
If you are stuck, below is a candidate implementation of the particle swarm in pure Python.

```python
# AlgorithmAfternoon.com
import random

def objective_function(x, y):
    """ Objective function f(x, y) = (1 - x)^2 + 100(y - x^2)^2 """
    return (1 - x) ** 2 + 100 * (y - x ** 2) ** 2

def initialize_particles(num_particles, bounds):
    """ Initialize particles with random positions and velocities """
    particles = []
    for _ in range(num_particles):
        particle = {
            'position': [random.uniform(bounds[dim][0], bounds[dim][1]) for dim in range(len(bounds))],
            'velocity': [random.uniform(-1, 1) for _ in range(len(bounds))],
            'best_position': None,
            'best_cost': float('inf')
        }
        particles.append(particle)
    return particles

def update_velocity(particle, global_best_position, w, c1, c2):
    """ Update velocity based on cognitive and social components """
    for i in range(len(particle['velocity'])):
        cognitive = c1 * random.random() * (particle['best_position'][i] - particle['position'][i])
        social = c2 * random.random() * (global_best_position[i] - particle['position'][i])
        particle['velocity'][i] = w * particle['velocity'][i] + cognitive + social

def update_position(particle, bounds):
    """ Update position based on velocity and bounds """
    for i in range(len(particle['position'])):
        particle['position'][i] += particle['velocity'][i]
        # Ensure particle stays within bounds
        particle['position'][i] = max(bounds[i][0], min(particle['position'][i], bounds[i][1]))

def particle_swarm_optimization(objective_function, bounds, num_particles, max_iter, w, c1, c2):
    """ Perform Particle Swarm Optimization """
    # Initialize particles
    particles = initialize_particles(num_particles, bounds)
    global_best_position = None
    global_best_cost = float('inf')

    for iteration in range(max_iter):
        for particle in particles:
            # Evaluate the objective function
            cost = objective_function(particle['position'][0], particle['position'][1])
            # Update personal best
            if cost < particle['best_cost']:
                particle['best_position'] = particle['position'][:]
                particle['best_cost'] = cost
                # Update global best
                if cost < global_best_cost:
                    global_best_position = particle['position'][:]
                    global_best_cost = cost

        # Update velocity and position
        for particle in particles:
            update_velocity(particle, global_best_position, w, c1, c2)
            update_position(particle, bounds)

        # Report best cost found in this iteration
        print(f"Iteration {iteration + 1}: Best Cost = {global_best_cost}")

    return global_best_position, global_best_cost

# Algorithm parameters
bounds = [(-2, 2), (-1, 3)]  # bounds for x and y
num_particles = 30
max_iter = 100
w = 0.5
c1 = 1.5
c2 = 1.5

# Run the Particle Swarm Optimization algorithm
best_position, best_cost = particle_swarm_optimization(objective_function, bounds, num_particles, max_iter, w, c1, c2)
print(f"Best solution: x = {best_position[0]}, y = {best_position[1]}, Cost = {best_cost}")
```
{{< /details >}}


## Mini-Book
**Update**: If you need more help, you might be interested in the new [Particle Swarm Mini-Book](/books/particle_swarm)
