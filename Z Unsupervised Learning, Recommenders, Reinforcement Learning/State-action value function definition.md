[[Bellman Equation]]
# The State-Action Value Function (Q-Function) in Reinforcement Learning

In reinforcement learning, a key quantity that algorithms will try to compute is the **state-action value function**, often denoted by the uppercase letter \( Q \). This function \( Q(s, a) \) gives the expected return if you start in state \( s \), take action \( a \), and then follow the optimal policy afterward.

## Definition and Circularity

The state-action value function \( Q(s, a) \) is defined as the return obtained by:
1. Starting in state \( s \).
2. Taking action \( a \) once.
3. Following the optimal policy from that point onward.

## Example: Mars Rover with Discount Factor \( \gamma = 0.5 \)

Recall the Mars Rover example with states and a discount factor \( \gamma = 0.5 \). Suppose the optimal policy is to go left from states 2, 3, and 4, and to go right from state 5.

### Calculating \( Q(s, a) \)

Let's compute \( Q(s, a) \) for different states and actions.

1. **State 2, Action Right**:
    - Sequence: \( s_2 \rightarrow s_3 \rightarrow s_2 \rightarrow s_1 \)
    - Rewards: 0, 0, 0, 100
    - Return: 
      $$
      0 + 0.5 \times 0 + 0.5^2 \times 0 + 0.5^3 \times 100 = 12.5
      $$
    - \( Q(s_2, \text{right}) = 12.5 \)

2. **State 2, Action Left**:
    - Sequence: \( s_2 \rightarrow s_1 \)
    - Rewards: 0, 100
    - Return: 
      $$
      0 + 0.5 \times 100 = 50
      $$
    - \( Q(s_2, \text{left}) = 50 \)

3. **State 4, Action Left**:
    - Sequence: \( s_4 \rightarrow s_3 \rightarrow s_2 \rightarrow s_1 \)
    - Rewards: 0, 0, 0, 100
    - Return:
      $$
      0 + 0.5 \times 0 + 0.5^2 \times 0 + 0.5^3 \times 100 = 12.5
      $$
    - \( Q(s_4, \text{left}) = 12.5 \)

To summarize the values of \( Q(s, a) \):

| State | Action | Q-Value |
|-------|--------|---------|
| 2     | Right  | 12.5    |
| 2     | Left   | 50      |
| 4     | Left   | 12.5    |
| ...   | ...    | ...     |

### Optimal Policy

Given the \( Q \)-values, the optimal policy \( \pi(s) \) can be derived by choosing the action \( a \) that maximizes \( Q(s, a) \) in each state \( s \).

For example:
- In state 2, the optimal action is Left since \( Q(s_2, \text{left}) = 50 \) is greater than \( Q(s_2, \text{right}) = 12.5 \).
- In state 4, the optimal action is Left since \( Q(s_4, \text{left}) = 12.5 \).

### Conclusion

The state-action value function \( Q(s, a) \) provides the expected return for taking action \( a \) in state \( s \) and then behaving optimally thereafter. By computing \( Q(s, a) \) for all states and actions, we can derive the optimal policy \( \pi(s) \), which maximizes the expected return.

In the next video, we will explore specific reinforcement learning algorithms to compute the \( Q \)-function despite the seemingly circular definition. Stay tuned!
