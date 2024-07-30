# Bellman Equation in Reinforcement Learning

## Summary
If you can compute the state-action value function $Q(s, a)$, then you can pick the best action from any state $s$ by choosing the action $a$ that maximizes $Q(s, a)$. The question is, how do you compute these values $Q(s, a)$? In reinforcement learning, there's a key equation called the **Bellman equation** that helps us compute the state-action value function.

## Bellman Equation

### Definition
As a reminder, $Q(s, a)$ is defined as the return if we start in state $s$, take action $a$ once, and then behave optimally afterward.

### Notation
- $s$: Current state
- $r(s)$: Reward of the current state $s$
- $a$: Current action taken in state $s$
- $s'$: State reached after taking action $a$ from state $s$
- $a'$: Action that might be taken in state $s'$

The notation convention is that $s, a$ correspond to the current state and action, while $s', a'$ correspond to the next state and next action.

### The Bellman Equation
The Bellman equation is:
$$
Q(s, a) = r(s) + \gamma \max_{a'} Q(s', a')
$$
where $\gamma$ is the discount factor.

### Examples

#### Example 1: $Q(s_2, \text{right})$
- Current state: $s_2$
- Action: Go right
- Next state $s'$: $s_3$

Applying the Bellman equation:
$$
Q(s_2, \text{right}) = r(s_2) + \gamma \max_{a'} Q(s_3, a')
$$
Given:
- $r(s_2) = 0$
- $\gamma = 0.5$
- $Q(s_3, \text{left}) = 25$
- $Q(s_3, \text{right}) = 6.25$

Calculate:
$$
Q(s_2, \text{right}) = 0 + 0.5 \times \max(25, 6.25) = 0 + 0.5 \times 25 = 12.5
$$

#### Example 2: $Q(s_4, \text{left})$
- Current state: $s_4$
- Action: Go left
- Next state $s'$: $s_3$

Applying the Bellman equation:
$$
Q(s_4, \text{left}) = r(s_4) + \gamma \max_{a'} Q(s_3, a')
$$
Given:
- $r(s_4) = 0$
- $\gamma = 0.5$
- $Q(s_3, \text{left}) = 25$
- $Q(s_3, \text{right}) = 6.25$

Calculate:
$$
Q(s_4, \text{left}) = 0 + 0.5 \times \max(25, 6.25) = 0 + 0.5 \times 25 = 12.5
$$

### Terminal States
In terminal states, the Bellman equation simplifies to:
$$
Q(s, a) = r(s)
$$
because there is no state $s'$.

### Intuition Behind the Bellman Equation
The Bellman equation captures the idea that the total return in a reinforcement learning problem can be broken down into:
1. The immediate reward $r(s)$.
2. The discounted return from the next state $s'$, which is $\gamma \max_{a'} Q(s', a')$.

This breakdown reflects the essence of the reinforcement learning problem: combining immediate rewards with future returns.

#### Example Recap: $Q(s_4, \text{left})$
- Rewards sequence: $0$ (at $s_4$), $0$ (at $s_3$), $0$ (at $s_2$), $100$ (at terminal state)
- Total return:
$$
0 + 0.5 \times 0 + 0.5^2 \times 0 + 0.5^3 \times 100 = 12.5
$$
The Bellman equation breaks this into:
- Immediate reward: $r(s_4) = 0$
- Discounted return from $s_3$:
$$
\gamma \times \max_{a'} Q(s_3, a') = 0.5 \times 25 = 12.5
$$

### Conclusion
The Bellman equation is fundamental in reinforcement learning as it provides a recursive way to compute the state-action value function $Q(s, a)$. This equation helps in breaking down the returns into immediate and future rewards, guiding the learning algorithm to optimize decisions over time.
[[Random Stochastic Environment]]