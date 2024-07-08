#Machinelearning

**Overview:** Gradient descent is<mark style="background: #D2B3FFA6;"> an optimization algorithm used to find the values of parameters that minimize the cost function</mark>, crucial for training machine learning models such as linear regression and neural networks.

1. **Initial Guesses:**
    
    - Start with initial values for parameters $w$ and $b$, often set to 0.
2. **Iterative Process:**
    
    - Adjust parameters $w$ and $b$ iteratively to reduce the cost function $J(w, b)$.
    - The goal is to minimize $J(w, b)$ to find the optimal parameters.
3. **Visualization:**
    
    - Imagine the cost function $J(w, b)$ as a surface where the horizontal axes are $w$ and $b$, and the vertical axis is $J$.
    - The objective is to find the lowest point on this surface, representing the minimum cost.
4. **Analogy:**
    
    - Think of the surface as a hilly landscape.
    - Starting at a point on a hill, the goal is to descend to the lowest valley by taking steps in the steepest descent direction.
5. **Steps in Gradient Descent:**
    
    - **Initialization:** Begin with initial values of $w$ and $b$.
    - **Compute Gradient:** Calculate the gradient (slope) of $J(w, b)$ at the current point.
    - **Update Parameters:** Adjust $w$ and $b$ in the direction of the negative gradient.
    - **Repeat:** Continue the process <mark style="background: #D2B3FFA6;">until convergence</mark>, when changes in $J(w, b)$ become minimal.
6. **Mathematical Details:**
    
    - Gradient descent update rule:
$$
w := w - \alpha \frac{\partial J(w, b)}{\partial w}
$$
$$
	b := b - \alpha \frac{\partial J(w, b)}{\partial b}

$$
	    $\alpha$ is the learning rate, determining the step size.
	![[Pasted image 20240707120042.png]]
1. **Local Minima:**
    
    - The [[Cost Function]] may have multiple valleys (local minima).
    - Gradient descent can get stuck in a local minimum based on the starting point.
    - Different starting points can lead to different local minima.
8. **Conclusion:**
    
    - Gradient descent is essential for finding parameters that minimize the cost function.
    - The algorithm iteratively updates parameters based on the gradient, aiming to reach the lowest point on the cost function surface for the best model fit.

[[Gradient Descent Intuition]]