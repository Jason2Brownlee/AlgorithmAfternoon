---
title: Chapter 2 - Temperature and Cooling Schedules
---
# Chapter 2: Temperature and Cooling Schedules

## Section 1: Role of Temperature in Simulated Annealing

In the world of optimization algorithms, simulated annealing stands out as a powerful and versatile technique. At the heart of this algorithm lies a key concept: temperature. In this section, we'll dive into the role of temperature in simulated annealing, exploring how it influences the search process and enables the algorithm to find optimal solutions efficiently.

### 1.1 Concept of Temperature in Optimization

In simulated annealing, temperature serves as a control parameter that guides the exploration of the search space. This metaphorical use of temperature is inspired by the annealing process in metallurgy, where a material is heated and then slowly cooled to alter its properties.

Higher temperatures in simulated annealing allow for more extensive exploration of the search space. When the temperature is high, the algorithm is more likely to accept solutions that may not immediately improve the objective function. This willingness to explore helps the algorithm escape local minima—suboptimal solutions that are better than their immediate neighbors but not necessarily the best overall.

As the temperature decreases, the algorithm becomes more focused on fine-tuning the current solutions. It becomes less likely to accept worse solutions, instead concentrating on improving the existing ones.

### 1.2 Temperature's Effect on Solution Acceptance

The simulated annealing algorithm uses the Metropolis criterion to decide whether to accept a new solution. If the new solution improves the objective function, it is always accepted. However, if the new solution is worse, it is accepted with a probability based on the current temperature and the magnitude of the objective function change.

The acceptance probability is calculated using the following formula:

```
P(accept) = e^(-ΔE / T)
```

Here, `ΔE` represents the change in the objective function value between the current and new solutions, and `T` is the current temperature.

Let's consider an example to illustrate the effect of temperature on acceptance probability. Suppose we have a current solution with an objective function value of 100, and a new solution with a value of 120. If the temperature is high, say 1000, the acceptance probability for this worse solution would be:

```
P(accept) = e^(-(120 - 100) / 1000) ≈ 0.98
```

In this case, the algorithm is very likely to accept the worse solution, allowing for further exploration.

Now, let's consider the same scenario but with a lower temperature of 10:

```
P(accept) = e^(-(120 - 100) / 10) ≈ 0.14
```

With a lower temperature, the acceptance probability for the worse solution is much smaller, making it less likely to be accepted.

This Temperature-dependent acceptance probability is a key feature of simulated annealing. By occasionally accepting worse solutions, the algorithm can escape local minima and explore more of the search space, increasing the chances of finding the global optimum.



## Section 2: Types of Cooling Schedules

### 2.1 Overview of Cooling Schedules

In simulated annealing, the cooling schedule plays a crucial role in controlling how the temperature decreases over time. The choice of cooling schedule can significantly impact the algorithm's performance and its ability to find optimal solutions. There are three main types of cooling schedules: linear, exponential, and logarithmic. Each has its own characteristics and is suited for different optimization scenarios.

### 2.2 Linear Cooling Schedule

The linear cooling schedule is the simplest of the three. In this approach, the temperature decreases by a constant amount at each iteration. The formula for updating the temperature is:

```python
T_new = T_current - α
```

Here, `α` is a constant that determines the rate of temperature decrease.

The linear cooling schedule is straightforward to implement and understand. However, it has some potential drawbacks. The constant rate of cooling may lead to premature convergence, where the algorithm gets stuck in a local minimum before adequately exploring the search space. Additionally, the linear schedule may not allow enough exploration in later stages when fine-tuning the solution is crucial.

```python
def linear_cooling(T_start, alpha, iteration):
    return T_start - alpha * iteration
```

### 2.3 Exponential Cooling Schedule

The exponential cooling schedule is a more commonly used approach that offers a more controlled temperature decrease compared to the linear schedule. In this method, the temperature is reduced by a constant factor at each iteration. The formula for updating the temperature is:

```python
T_new = T_current * α
```

Here, `α` is a constant factor between 0 and 1 that determines the rate of temperature decrease.

The exponential cooling schedule allows for slower cooling and more exploration in later stages of the optimization process. By carefully choosing the value of `α`, you can balance exploration and exploitation, allowing the algorithm to escape local minima and converge to a high-quality solution.

```python
def exponential_cooling(T_start, alpha, iteration):
    return T_start * (alpha ** iteration)
```

When implementing the exponential cooling schedule, it's essential to consider the value of `α`. A smaller value of `α` will result in slower cooling, allowing more exploration but potentially slowing down convergence. On the other hand, a larger value of `α` will lead to faster cooling, which may compromise the algorithm's ability to find the global optimum.

### 2.4 Logarithmic Cooling Schedule

The logarithmic cooling schedule is less common but can be useful for problems that require fine-tuning in the final stages of optimization. In this approach, the temperature decreases according to the logarithm of the current iteration. The formula for updating the temperature is:

```python
T_new = C / log(1 + i)
```

Here, `C` is a constant that determines the initial temperature, and `i` is the current iteration.

The logarithmic cooling schedule provides a slower temperature decrease in later stages, which can help prevent the algorithm from getting stuck in local minima. This property makes it particularly useful for problems where fine-tuning the solution is critical.

```python
def logarithmic_cooling(C, iteration):
    return C / math.log(1 + iteration)
```

However, the logarithmic cooling schedule is more complex to implement compared to the linear and exponential schedules. It may also slow down convergence in some cases, especially if the initial temperature is set too high.



## Section 3: Implementing a Temperature Function

### 3.1 Designing a Temperature Function

When designing a temperature function for simulated annealing, it's essential to consider several key factors. The starting temperature plays a crucial role in balancing exploration and exploitation. A higher starting temperature allows for more exploration of the search space, while a lower temperature focuses on exploiting the current best solution. The choice of starting temperature depends on the specific requirements of the optimization problem at hand.

Another important consideration is the total number of iterations. This decision involves a trade-off between computational resources and solution quality. More iterations generally lead to better solutions but at the cost of increased computation time. The number of iterations is also closely related to the chosen cooling schedule, as some schedules may require more iterations to reach the desired solution quality.

When adapting the temperature function to the optimization problem, it's necessary to consider the problem's complexity and landscape. Problems with a more complex or rugged landscape may require a slower cooling rate to allow for adequate exploration. On the other hand, simpler problems may benefit from a faster cooling rate to speed up convergence. Adjusting the parameters of the temperature function based on the problem characteristics can greatly improve the algorithm's performance.

### 3.2 Evaluating the Effectiveness of a Temperature Function

Evaluating the effectiveness of a temperature function involves assessing the quality of the solutions obtained and the convergence rate of the algorithm. One common metric for solution quality is the objective function value. In cases where the optimal solution is known, we can measure how close the algorithm converges to the known optimum.

The convergence rate can be evaluated by tracking the number of iterations required to reach a satisfactory solution. Additionally, measuring the computational time can provide insights into the efficiency of the temperature function.

To compare different temperature functions, it's valuable to apply them to the same optimization problem and analyze the trade-off between solution quality and convergence speed. This comparative analysis can help in selecting the most appropriate temperature function for the specific problem at hand.



## Exercises

In these exercises, you will explore the impact of temperature and cooling schedules on the exploration of the search space in simulated annealing. By modifying the sample point generation code and visualizing the results, you will gain insights into how different cooling schedules and temperatures influence the algorithm's behavior.

### Exercise 1: Implementing Cooling Schedules

Modify the sample point generation code from the exercise in Chapter 1 to incorporate cooling schedules that adjust the spread of generated points over iterations. Implement the following cooling schedules:

1. Linear Cooling Schedule:
   - Implement the `linear_cooling` function that takes the starting temperature (`T_start`), cooling rate (`alpha`), and current iteration (`iteration`) as parameters.
   - The function should return the updated temperature based on the linear cooling formula: `T_new = T_start - alpha * iteration`.

2. Exponential Cooling Schedule:
   - Implement the `exponential_cooling` function that takes the starting temperature (`T_start`), cooling rate (`alpha`), and current iteration (`iteration`) as parameters.
   - The function should return the updated temperature based on the exponential cooling formula: `T_new = T_start * (alpha ** iteration)`.

3. Logarithmic Cooling Schedule:
   - Implement the `logarithmic_cooling` function that takes a constant (`C`) and the current iteration (`iteration`) as parameters.
   - The function should return the updated temperature based on the logarithmic cooling formula: `T_new = C / log(1 + iteration)`.

### Exercise 2: Temperature-Controlled Point Generation

Modify the `generate_sample_points` function from Chapter 1 to generate new points based on the current temperature. The function should take the following parameters:

- `num_points`: The number of sample points to generate.
- `x_min`: The minimum value of the range for generating points.
- `x_max`: The maximum value of the range for generating points.
- `temperature`: The current temperature value.

Inside the function, use `numpy.random.normal` to generate `num_points` random values from a normal distribution centered at the midpoint of the range (`(x_min + x_max) / 2`) and with a standard deviation proportional to the current temperature.

As the temperature decreases, the standard deviation should decrease, resulting in a narrower spread of generated points. This behavior mimics how higher temperatures allow for broader exploration in simulated annealing.

### Exercise 3: Visualizing Temperature Effects

Create a visualization that demonstrates how the distribution of points changes with each cooling schedule over multiple iterations. Follow these steps:

1. Implement a function called `visualize_cooling_schedules` that takes the following parameters:
   - `num_iterations`: The total number of iterations to simulate.
   - `num_points`: The number of sample points to generate at each iteration.
   - `x_min`: The minimum value of the range for generating points.
   - `x_max`: The maximum value of the range for generating points.
   - `T_start`: The starting temperature for the cooling schedules.
   - `alpha`: The cooling rate for the linear and exponential cooling schedules.
   - `C`: The constant for the logarithmic cooling schedule.

2. Inside the function, create a plot with subplots for each cooling schedule (linear, exponential, logarithmic).

3. For each cooling schedule, iterate `num_iterations` times and perform the following steps:
   - Calculate the current temperature using the corresponding cooling schedule function.
   - Generate sample points using the `generate_sample_points` function with the current temperature.
   - Plot the generated points on the corresponding subplot.

4. Add labels, titles, and any other desired formatting to the subplots to clearly indicate the cooling schedule and iteration number.

5. Display the final plot showing the progression of point distributions for each cooling schedule over the specified number of iterations.

By completing these exercises, you will gain hands-on experience in implementing cooling schedules and visualizing their impact on the exploration of the search space. Observe how different cooling schedules affect the spread of generated points and consider their implications for the simulated annealing algorithm's behavior.

Experiment with different parameter values for the cooling schedules and observe how they influence the visualization. Discuss your findings and insights with your peers or in a group setting to deepen your understanding of temperature and cooling schedules in simulated annealing.


## Answers
{{< details "Show" >}}
### Exercise 1: Implementing Cooling Schedules

Here are the Python functions for the three different cooling schedules:

```python
import math

def linear_cooling(T_start, alpha, iteration):
    """ Calculate the temperature using a linear cooling schedule. """
    return T_start - alpha * iteration

def exponential_cooling(T_start, alpha, iteration):
    """ Calculate the temperature using an exponential cooling schedule. """
    return T_start * (alpha ** iteration)

def logarithmic_cooling(C, iteration):
    """ Calculate the temperature using a logarithmic cooling schedule. """
    # Ensure we never divide by zero
    return C / (1e-8 + math.log(1 + iteration))
```

### Exercise 2: Temperature-Controlled Point Generation

Let's modify the `generate_sample_points` function to generate points based on the current temperature:

```python
import numpy as np

def generate_sample_points(num_points, x_min, x_max, temperature):
    """ Generate sample points based on the current temperature. """
    # Calculate the midpoint of the range
    midpoint = (x_min + x_max) / 2
    # Generate points from a normal distribution centered at midpoint with std dev proportional to temperature
    sample_points = np.random.normal(midpoint, temperature, num_points)
    return sample_points
```

### Exercise 3: Visualizing Temperature Effects

Finally, we'll create a visualization to show how the distribution of points changes over iterations with each cooling schedule:

```python
import matplotlib.pyplot as plt
import math
import numpy as np

def linear_cooling(T_start, alpha, iteration):
    """ Calculate the temperature using a linear cooling schedule. """
    return T_start - alpha * iteration

def exponential_cooling(T_start, alpha, iteration):
    """ Calculate the temperature using an exponential cooling schedule. """
    return T_start * (alpha ** iteration)

def logarithmic_cooling(C, iteration):
    """ Calculate the temperature using a logarithmic cooling schedule. """
    return C / (1e-8 + math.log(1 + iteration))

def generate_sample_points(num_points, x_min, x_max, temperature):
    """ Generate sample points based on the current temperature. """
    # Calculate the midpoint of the range
    midpoint = (x_min + x_max) / 2
    # Generate points from a normal distribution centered at midpoint with std dev proportional to temperature
    sample_points = np.random.normal(midpoint, temperature, num_points)
    return sample_points

def visualize_cooling_schedules(num_iterations, num_points, x_min, x_max, T_start, alpha, C):
    """ Visualize the effect of different cooling schedules on point distributions. """
    plt.figure(figsize=(15, 5))

    # Prepare subplots for each cooling schedule
    schedules = ['Linear', 'Exponential', 'Logarithmic']
    for i, schedule in enumerate(schedules, 1):
        plt.subplot(1, 3, i)
        for iteration in range(num_iterations):
            if schedule == 'Linear':
                temperature = linear_cooling(T_start, alpha, iteration)
            elif schedule == 'Exponential':
                temperature = exponential_cooling(T_start, alpha, iteration)
            else:  # Logarithmic
                temperature = logarithmic_cooling(C, iteration)

            points = generate_sample_points(num_points, x_min, x_max, temperature)
            plt.scatter([iteration] * num_points, points, alpha=0.6, s=10)

        plt.title(f'{schedule} Cooling Schedule')
        plt.xlabel('Iteration')
        plt.ylabel('Point Distribution')

    plt.tight_layout()
    plt.show()

# Example usage
visualize_cooling_schedules(50, 100, -5, 5, 10, 0.1, 20)
```

This code plots the progression of point distributions for each cooling schedule over a specified number of iterations. It demonstrates the narrowing of point spreads as the temperature decreases, following each cooling schedule.

This setup allows us to visually compare the impact of different cooling strategies on the exploration capabilities of a simulated annealing-like algorithm.
{{< /details >}}


## Summary
Chapter 2 explored the crucial role of temperature and cooling schedules in Simulated Annealing (SA). The chapter explained how temperature serves as a control parameter, guiding the exploration of the search space and influencing the acceptance of new solutions. The Metropolis criterion was introduced, demonstrating how the acceptance probability of worse solutions is calculated based on the current temperature and the change in the objective function value. The chapter then explored three main types of cooling schedules: linear, exponential, and logarithmic. Each schedule's characteristics, implementation, and suitability for different optimization scenarios were discussed in detail. Finally, the chapter provided guidance on designing and evaluating the effectiveness of temperature functions, considering factors such as starting temperature, total iterations, and problem complexity.

### Key Takeaways
1. Temperature in SA controls the exploration of the search space, with higher temperatures allowing for more extensive exploration and lower temperatures focusing on fine-tuning solutions.
2. The choice of cooling schedule (linear, exponential, or logarithmic) significantly impacts the algorithm's performance and its ability to find optimal solutions.
3. Designing an effective temperature function involves considering the starting temperature, total iterations, and the complexity of the optimization problem.

### Exercise Encouragement
Get hands-on with temperature and cooling schedules by implementing the three main types of cooling schedules and visualizing their impact on the distribution of sample points over multiple iterations. This exercise will solidify your understanding of how temperature and cooling schedules influence the exploration of the search space in SA. Don't be afraid to experiment with different parameter values and observe their effects on the visualization. By completing these exercises, you'll gain valuable insights into the inner workings of SA and be well-equipped to apply this powerful optimization technique to real-world problems. Embrace the challenge, and let your curiosity guide you through this exciting exploration of temperature and cooling schedules in SA!

### Glossary:

- **Temperature**: A control parameter in SA that guides the exploration of the search space and influences the acceptance of new solutions.
- **Cooling Schedule**: The rate at which the temperature decreases over time in SA, controlling the balance between exploration and exploitation.
- **Linear Cooling Schedule**: A simple cooling schedule where the temperature decreases by a constant amount at each iteration.
- **Exponential Cooling Schedule**: A commonly used cooling schedule where the temperature is reduced by a constant factor at each iteration.
- **Logarithmic Cooling Schedule**: A cooling schedule where the temperature decreases according to the logarithm of the current iteration, useful for problems requiring fine-tuning in the final stages.
- **Metropolis Criterion**: The acceptance rule in SA that determines whether to accept a new solution based on the current temperature and the change in the objective function value.
- **Acceptance Probability**: The probability of accepting a new solution in SA, calculated using the Metropolis criterion.
- **Starting Temperature**: The initial temperature value in SA, which plays a crucial role in balancing exploration and exploitation.
- **Total Iterations**: The number of iterations performed in SA, influencing the computational resources required and the quality of the obtained solutions.
- **Problem Complexity**: The characteristics and landscape of the optimization problem, which can impact the choice of cooling schedule and temperature function parameters.

### Next Chapter:
In [Chapter 3](chapter03.md), we'll explore how new solutions are generated in Simulated Annealing and dive into the criteria for their acceptance or rejection, gaining a deeper understanding of the algorithm's decision-making process.



