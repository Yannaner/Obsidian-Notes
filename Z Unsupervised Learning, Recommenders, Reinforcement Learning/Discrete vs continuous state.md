

## Overview
Many robotic control applications, including the lunar lander application you work on in the practice lab, have continuous state spaces. Let's explore what that means and how to generalize the concepts we've discussed to these continuous state spaces.

## Discrete vs. Continuous State Spaces

### Discrete State Spaces
In the simplified Mars rover example, we used a discrete set of states. This means that the Mars rover could only be in one of six possible positions. For instance, the rover could be at position $1, 2, 3, 4, 5,$ or $6$.

### Continuous State Spaces
However, most robots can be in more than just a few discrete positions. They can be in any of a large number of continuously valued positions. 

#### Example: Mars Rover
If the Mars rover could be anywhere on a line, its position could be represented by a number ranging from 0 to 6 kilometers, where any number in between is valid. This represents a continuous state space, because the position could be, for example, $2.7$ kilometers or $4.8$ kilometers.

#### Example: Controlling a Car or Truck
Consider a toy truck, for example. If you're building a self-driving car or truck, the state of this vehicle might include a few numbers such as:
- $x$: Position in the x-direction
- $y$: Position in the y-direction
- $\theta$: Orientation (which way it is facing)

Assuming the truck stays on the ground, you don't need to worry about its height. The state might include:
- $x$
- $y$
- $\theta$: Orientation
- $\dot{x}$: Speed in the x-direction
- $\dot{y}$: Speed in the y-direction
- $\dot{\theta}$: Rate of turning (angular velocity)

Thus, for a truck, the state would comprise a vector of six numbers, each taking any value within its valid range. For example, $\theta$ should range between $0$ and $360$ degrees.

#### Example: Autonomous Helicopter
For an autonomous helicopter, the state includes its position and orientation. Here is a small toy helicopter for illustration.

The state would include:
- $x$: Position in the north-south direction
- $y$: Position in the east-west direction
- $z$: Height above ground

Additionally, the helicopter's orientation is typically captured with three more numbers:
- $\phi$: Roll (left or right tilt)
- $\theta$: Pitch (forward or backward tilt)
- $\psi$: Yaw (compass direction)

Thus, the state of the helicopter includes:
- Position: $x, y, z$
- Orientation: $\phi, \theta, \psi$

To control the helicopter, we also need to know its speed and angular velocities:
- $\dot{x}$: Speed in the x-direction
- $\dot{y}$: Speed in the y-direction
- $\dot{z}$: Speed in the z-direction
- $\dot{\phi}$: Angular velocity (rate of roll change)
- $\dot{\theta}$: Angular velocity (rate of pitch change)
- $\dot{\psi}$: Angular velocity (rate of yaw change)

### Continuous State Markov Decision Process (MDP)
In continuous state reinforcement learning problems or continuous state MDPs, the state of the problem is not just one of a small number of discrete values. Instead, it's a vector of numbers, any of which can take a large number of values.

## Practice Lab: Lunar Lander Application
In the practice lab, you will implement a reinforcement learning algorithm applied to a simulated lunar lander application. Landing something on the moon in simulation will be another example of a continuous state application.

Next, let's explore what this lunar lander application entails.
