


## Recap of Logistic Regression Model

1. **Compute `z`:**

    $$
    z = w \cdot x + b
    $$

2. **Apply Sigmoid Function `g` to `z`:**

    $$
    f(x) = g(z) = \frac{1}{1 + e^{-z}}
    $$
    where $z = w \cdot x + b$.

3. **Interpretation:**

    - $f(x)$ represents the probability that $y = 1$ given $x$ and parameters $w$ and $b$.
    - Typically, a threshold of $0.5$ is used to predict class labels:
        $$
        \hat{y} = 
        \begin{cases} 
        1 & \text{if } f(x) \geq 0.5 \\
        0 & \text{if } f(x) < 0.5 
        \end{cases}
        $$

## Understanding the Decision Boundary

- **When $f(x) \ge 0.5$:**
    $$
    f(x) \ge 0.5 \implies g(z) \ge 0.5
    $$
    - Since $g(z) = \frac{1}{1 + e^{-z}}$, $g(z) \ge 0.5$ when $z \ge 0$.
    - Therefore, the model predicts $\hat{y} = 1$ when $w \cdot x + b \ge 0$.
  
- **When $w \cdot x + b = 0$:**
    - This defines the **decision boundary**, where the model is equally likely to predict $0$ or $1$.

## Visualization with Two Features

- **Example Parameters:**
    $$
    w_1 = 1, w_2 = 1, b = -3
    $$
    - Decision boundary: $w_1 x_1 + w_2 x_2 + b = 0$
    - For these parameters: $x_1 + x_2 - 3 = 0$, or $x_1 + x_2 = 3$
    - Points to the right of this line: $\hat{y} = 1$
    - Points to the left of this line: $\hat{y} = 0$

## Non-linear Decision Boundaries

- **Polynomial Features:**
    - **Example:** $z = w_1 x_1^2 + w_2 x_2^2 + b$
    - **Parameters:** $w_1 = 1, w_2 = 1, b = -1$
    - Decision boundary: $x_1^2 + x_2^2 = 1$
    - Points outside the circle: $\hat{y} = 1$
    - Points inside the circle: $\hat{y} = 0$

- **More Complex Boundaries:**
    - Using higher-order polynomial terms can create more intricate boundaries:
        $$
        z = w_1 x_1 + w_2 x_2 + w_3 x_1^2 + w_4 x_1 x_2 + w_5 x_2^2
        $$
    - This can result in decision boundaries that are ellipses or even more complex shapes.

## Summary

- **Decision Boundary:**
    - Defines where the logistic regression model switches from predicting $\hat{y} = 0$ to $\hat{y} = 1$.
    - Linear boundaries for simple features; non-linear for polynomial features.
  
- **Upcoming Lab:**
    - Implementation of decision boundaries in code with visualizations.

In the next video, we'll explore how to train a logistic regression model, starting with the cost function and applying gradient descent.
