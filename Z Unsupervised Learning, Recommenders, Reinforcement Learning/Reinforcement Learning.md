# Introduction to Reinforcement Learning

Welcome to the final week of our machine learning specialization! While it’s a bit bittersweet to approach the end, I’m excited to share some fascinating ideas about reinforcement learning with you. Though not widely applied in commercial applications yet, reinforcement learning is a cornerstone of machine learning with significant ongoing research.

## What is Reinforcement Learning?

Let’s start with an example: the Stanford autonomous helicopter, which weighs 32 pounds and is equipped with an onboard computer, GPS, accelerometers, gyroscopes, and a magnetic compass for accurate positioning. Imagine you need to write a program to fly this helicopter using joysticks. Every second, you receive data about the helicopter’s position, orientation, and speed, and you must decide how to move the control sticks to keep it balanced in the air.

### Autonomous Helicopter Example

Here’s a fun video demonstrating the Stanford autonomous helicopter flying under the control of a reinforcement learning algorithm. Using reinforcement learning, we got the helicopter to perform aerobatic maneuvers, like flying upside down.

## Key Concepts in Reinforcement Learning

### State and Action

In reinforcement learning:
- **State (s)**: The position, orientation, speed, etc., of the helicopter.
- **Action (a)**: The movement of the control sticks to keep the helicopter balanced.

The task is to find a function that maps the state (s) to an action (a) to maintain flight.

### Supervised Learning vs. Reinforcement Learning

You might consider using supervised learning to solve this problem by collecting state-action pairs from an expert pilot. However, this approach is impractical due to the ambiguity in determining the exact optimal action for each state. Instead, we use reinforcement learning.

### Reward Function

A crucial element in reinforcement learning is the **reward function**, which indicates when the helicopter is performing well or poorly. This is similar to training a dog:
- **Positive reward**: When the helicopter is flying well, give it a reward (e.g., +1).
- **Negative reward**: When it crashes or performs poorly, give it a large negative reward (e.g., -1000).

The algorithm learns to maximize positive rewards and minimize negative ones.

## Training a Robotic Dog

Using reinforcement learning, we trained a robotic dog to navigate obstacles by rewarding it for making progress towards a goal. This method does not require specifying the exact actions to take; instead, it learns the optimal actions through rewards.

## Applications of Reinforcement Learning

Reinforcement learning has been applied in various fields, including:
- **Robotics**: Controlling robots to perform tasks.
- **Factory optimization**: Maximizing throughput and efficiency.
- **Financial trading**: Optimizing the execution of large trades.
- **Game playing**: Achieving high performance in games like chess, Go, and video games.

# The return



## Analogy: Immediate vs. Delayed Rewards

Imagine you have a $5 bill at your feet and a $10 bill half an hour across town. Which one is more appealing? Although $10 is more valuable, the convenience of picking up the $5 bill immediately might make it more attractive. The concept of return in reinforcement learning captures this idea: rewards obtained sooner are generally more valuable than those that are delayed.

## Mars Rover Example

Consider a Mars Rover starting from state 4 and moving left:
- At state 4: Reward = 0
- At state 3: Reward = 0
- At state 2: Reward = 0
- At state 1 (terminal state): Reward = 100

### Discount Factor

The return is the sum of these rewards, adjusted by the **discount factor** (γ), a value slightly less than 1. For this example, let’s use 0.9:
- Reward at first step: 0
- Reward at second step: γ × 0 = 0.9 × 0
- Reward at third step: γ^2 × 0 = 0.81 × 0
- Reward at fourth step: γ^3 × 100 = 0.729 × 100 = 72.9

The general formula for the return is:

\[ G = R_1 + γ \times R_2 + γ^2 \times R_3 + γ^3 \times R_4 + \dots \]

### Impatience of the Algorithm

The discount factor makes the reinforcement learning algorithm a bit impatient:
- Immediate rewards are fully counted.
- Future rewards are progressively discounted.

Common choices for the discount factor are numbers close to 1, such as 0.9, 0.99, or 0.999. For illustration, let’s use a discount factor of 0.5. This heavily discounts future rewards:
- For state 4 to 1: \( 0 + 0.5 \times 0 + 0.5^2 \times 0 + 0.5^3 \times 100 = 12.5 \)

## Financial Interpretation

In finance, the discount factor can represent the interest rate or the time value of money. A dollar today is worth more than a dollar in the future because you can invest it to earn interest.

## Returns Based on Actions

### Example 1: Always Go Left
If the rover always goes left:
- Starting from state 4: Return = 12.5
- Starting from state 3: Return = 25
- Starting from state 2: Return = 50
- Starting from state 1: Return = 100

### Example 2: Always Go Right
If the rover always goes right:
- Starting from state 4: Return = 10
- Starting from state 3: Return = 20
- Starting from state 2: Return = 5
- Starting from state 1: Return = 2.5

### Mixed Strategy
If the rover goes left from states 2, 3, and 4, but right from state 5:
- Starting from state 4: Return = 12.5
- Starting from state 3: Return = 25
- Starting from state 2: Return = 50
- Starting from state 1: Return = 100
- Starting from state 5: Return = 20

## Negative Rewards

For systems with negative rewards, the discount factor incentivizes pushing negative rewards as far into the future as possible. For example, paying someone $10 in the future is preferable to paying $10 today due to the time value of money.

## Summary

The return in reinforcement learning is the sum of the rewards, adjusted by the discount factor, where future rewards are weighted less. This concept is crucial for evaluating and comparing different sequences of actions.

Next, we’ll formal

