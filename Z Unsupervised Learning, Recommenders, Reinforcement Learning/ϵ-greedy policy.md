# Reinforcement Learning: Epsilon-Greedy Policy

## Introduction
When developing a learning algorithm, such as for a lunar lander, we often face the challenge of choosing actions while still learning to approximate $Q(s, a)$. A common strategy to address this is the Epsilon-greedy policy.

## Epsilon-Greedy Policy

### Algorithm Overview
In the algorithm you saw earlier, one step involves taking actions in the lunar lander. While learning, we don't know the best action to take in every state because we don't have a good estimate of $Q(s, a)$ yet. So, how do we take actions during learning?

### Options for Action Selection
1. **Greedy Action Selection**
    - In state $s$, pick action $a$ that maximizes $Q(s, a)$.
    - This approach might work, but it isn't the best.

2. **Epsilon-Greedy Action Selection**
    - With probability $0.95$, pick the action that maximizes $Q(s, a)$.
    - With probability $0.05$, pick an action $a$ randomly.

#### Why Random Actions?
Suppose $Q(s, a)$ was initialized randomly, leading the algorithm to think firing the main thruster is never a good idea. If the neural network parameters were initialized so that $Q(s, \text{main})$ is always very low, it would never try firing the main thruster. As a result, it would never learn that firing the main thruster is sometimes a good idea. Option 2, however, allows for a small probability of trying different actions, helping the neural network overcome any initial misconceptions.

### Exploration and Exploitation
- **Exploration**: Trying out different actions to learn more about them.
- **Exploitation**: Taking actions that maximize $Q(s, a)$ based on current knowledge.

The Epsilon-greedy policy balances exploration and exploitation by exploring $\epsilon$ fraction of the time and exploiting $1 - \epsilon$ fraction of the time.

### Adaptive Epsilon
Another trick in reinforcement learning is to start with a high $\epsilon$ (e.g., $\epsilon = 1.0$) and gradually decrease it (e.g., down to $0.01$). Initially, actions are picked completely at random, and over time, actions are chosen based on improving estimates of the $Q$-function.

$$
\epsilon \text{-greedy policy}:
\begin{cases}
\text{With probability } 1 - \epsilon, & \text{choose action that maximizes } Q(s, a) \\
\text{With probability } \epsilon, & \text{choose a random action}
\end{cases}
$$

### Hyperparameter Sensitivity
Reinforcement learning algorithms are often more sensitive to hyperparameters compared to supervised learning algorithms. For instance, if $\epsilon$ is not well-tuned, the algorithm might take significantly longer to learn, sometimes by a factor of 10 or 100.

In the practice lab, you'll implement the algorithm with a more efficient neural network architecture and an Epsilon-greedy exploration policy. This combination should work well on the lunar lander exercise.

### Further Algorithm Refinements
Optional refinements such as mini-batching and soft updates can make the algorithm run faster. These refinements are not necessary to complete the practice lab, but they can enhance learning efficiency.

## Conclusion
The Epsilon-greedy policy is a common approach in reinforcement learning to balance exploration and exploitation. By starting with a high $\epsilon$ and gradually reducing it, the learning algorithm can effectively explore the action space and improve its estimates of the $Q$-function.
