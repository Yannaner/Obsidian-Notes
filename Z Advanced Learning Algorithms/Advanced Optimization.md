# Adam Optimization Algorithm

Adaptive Moment Estimation
There are different alpha value to train the model
   ```python
   model.compile(optimizer=tf.keras.optimizers.Adam(learning_rate=1e-3), ...)```
This method can adjust alpha value accordingly
Work faster than gradient descent
## Gradient Descent Recap
Recall the expression for one step of gradient descent:
$$ w_j = w_j - \alpha \frac{\partial J}{\partial w_j} $$
where \( \alpha \) is the learning rate.

### Visualization
In a contour plot of the cost function \( J \) with ellipses representing the contours, the minimum of this cost function is at the center of the ellipses. Starting gradient descent at a point, if \( \alpha \) is small, each step takes you a little further in the direction of the gradient:
1. One step in the direction of the gradient.
2. Another step, and so on.

If each step of gradient descent is going in the same direction, you might wonder if increasing \( \alpha \) could make it take bigger steps and reach the minimum faster.

## The Adam Algorithm
The Adam algorithm can automatically adjust the learning rate \( \alpha \):
- If the learning rate is too small and the steps are tiny, Adam increases \( \alpha \).
- If the learning rate is too large and the steps oscillate, Adam decreases \( \alpha \).

Adam stands for Adaptive Moment Estimation. It does not use a single global learning rate but rather different learning rates for each parameter of the model:
- For parameters \( w_1, w_2, \ldots, w_{10} \) and \( b \), Adam uses \( \alpha_1, \alpha_2, \ldots, \alpha_{10} \) for \( w_1 \) to \( w_{10} \), and \( \alpha_{11} \) for \( b \).

### Intuition
- If a parameter \( w_j \) or \( b \) keeps moving in the same direction, Adam increases the learning rate for that parameter.
- If a parameter oscillates, Adam decreases the learning rate for that parameter.

### Implementation
To use the Adam optimizer in code:
1. Define the model as before.
2. Compile the model, specifying the optimizer as `tf.keras.optimizers.Adam` with an initial learning rate. For example:
   ```python
   model.compile(optimizer=tf.keras.optimizers.Adam(learning_rate=1e-3), ...)
