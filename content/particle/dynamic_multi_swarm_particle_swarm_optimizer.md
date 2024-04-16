# Dynamic Multi-Swarm Particle Swarm Optimizer

## Name

Dynamic Multi-Swarm Particle Swarm Optimizer (DMSPSO), Dynamic Multi-Swarm PSO, DMS-PSO

## Taxonomy

Dynamic Multi-Swarm Particle Swarm Optimizer is a variant of Particle Swarm Optimization (PSO), which belongs to the field of Swarm Intelligence, a subfield of Computational Intelligence and Biologically Inspired Computation. It is closely related to other PSO variants such as Multi-Swarm PSO and Dynamic PSO.

- Computational Intelligence
  - Biologically Inspired Computation
    - Swarm Intelligence
      - Particle Swarm Optimization (PSO)
        - Dynamic Multi-Swarm Particle Swarm Optimizer (DMSPSO)

## Strategy

The Dynamic Multi-Swarm Particle Swarm Optimizer (DMSPSO) is designed to address the challenges of premature convergence and stagnation in standard PSO by dynamically maintaining multiple swarms that interact and evolve over the course of the optimization process.

### Dynamic Swarm Creation and Removal

DMSPSO starts with a single swarm, but as the optimization progresses, it dynamically creates new swarms when certain criteria are met, such as when the diversity of a swarm falls below a predefined threshold. Conversely, swarms that have converged or stagnated are removed to free up computational resources and maintain the overall efficiency of the algorithm.

### Swarm Interaction and Information Exchange

The multiple swarms in DMSPSO interact and exchange information to collaboratively search for the global optimum. This interaction is facilitated through the sharing of the global best position found by each swarm. By allowing swarms to communicate and learn from each other, DMSPSO aims to strike a balance between exploration and exploitation, preventing premature convergence while still efficiently converging towards promising regions of the search space.

### Dynamic Swarm Size Adjustment

DMSPSO also incorporates a mechanism to dynamically adjust the size of each swarm based on its performance and contribution to the overall optimization process. Swarms that consistently find better solutions are allocated more particles, while underperforming swarms have their size reduced. This adaptive resource allocation ensures that computational efforts are focused on the most promising swarms, enhancing the overall efficiency of the algorithm.

## Procedure

Data Structures:
- Swarm: A collection of particles, each representing a candidate solution
- Particle: Represents a candidate solution, with attributes such as position, velocity, and personal best position
- Global Best Position: The best position found by any particle across all swarms

Parameters:
- Maximum number of swarms
- Minimum and maximum swarm size
- Convergence threshold
- Diversity threshold
- Swarm creation probability
- Swarm removal probability
- Maximum iterations

Pseudocode:
1. Initialize a single swarm with a fixed number of particles
2. While the stopping criteria are not met:
   1. For each swarm:
      1. Update the position and velocity of each particle based on PSO rules
      2. Evaluate the fitness of each particle
      3. Update the personal best position of each particle
      4. Update the global best position of the swarm
   2. For each swarm:
      1. Calculate the diversity of the swarm
      2. If the diversity is below the diversity threshold:
         1. Create a new swarm with a probability based on the swarm creation probability
         2. Initialize the new swarm with particles from the current swarm and random particles
      3. If the swarm has converged (based on the convergence threshold):
         1. Remove the swarm with a probability based on the swarm removal probability
   3. Adjust the size of each swarm based on its performance
   4. Share the global best position among all swarms
3. Return the global best position found across all swarms

## Considerations

Advantages:
- Addresses the problem of premature convergence and stagnation in standard PSO
- Dynamically adapts to the optimization landscape by creating and removing swarms as needed
- Efficiently allocates computational resources to promising swarms through dynamic swarm size adjustment

Disadvantages:
- Introduces additional parameters that need to be tuned, such as the maximum number of swarms, diversity threshold, and swarm creation/removal probabilities
- The dynamic nature of the algorithm can lead to increased computational complexity compared to standard PSO
- The effectiveness of the algorithm may be sensitive to the choice of parameter values, requiring careful tuning for each problem

## Heuristics

### Parameter Setting

- The maximum number of swarms should be set based on the complexity of the problem and available computational resources. A higher number of swarms can lead to better exploration but increases computational costs.
- The minimum and maximum swarm sizes should be chosen to balance the trade-off between exploration and exploitation. Larger swarms tend to explore more, while smaller swarms focus on exploitation.
- The convergence threshold should be set based on the desired level of convergence and the problem's characteristics. A lower threshold will result in more fine-grained optimization but may increase the number of iterations required.
- The diversity threshold should be set to maintain a sufficient level of diversity within each swarm. A higher threshold will trigger the creation of new swarms more frequently, promoting exploration.

### Swarm Creation and Removal

- The swarm creation probability should be set to control the frequency of new swarm creation. A higher probability will result in more swarms being created, which can be beneficial for complex problems with many local optima.
- The swarm removal probability should be set to remove converged or stagnant swarms efficiently. A higher probability will result in more aggressive removal of underperforming swarms, freeing up resources for more promising swarms.

### Performance Monitoring

- Monitor the progress of each swarm and the overall optimization process to identify any stagnation or premature convergence issues. If the global best position does not improve for a significant number of iterations, consider adjusting the algorithm parameters or introducing additional diversity mechanisms.
- Keep track of the number of swarms and their sizes throughout the optimization process. If the number of swarms grows too large or the sizes of the swarms become imbalanced, it may indicate the need to adjust the swarm creation and removal probabilities or the dynamic swarm size adjustment mechanism.
