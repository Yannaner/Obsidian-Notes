#### Key Points

1. **Gradient Descent Rule Recap**
    
    - Recall the gradient descent update rule:
    
  
    $$w = w - \alpha \frac{\partial J}{\partial w} $$$$b = b - \alpha \frac{\partial J}{\partial b}$$
    
    - One crucial parameter to set is the learning rate $\alpha$.
2. **Monitoring the Cost Function**
    
    - To ensure gradient descent is working well, plot the cost function $J$, calculated on the training set, after each iteration.
    - The horizontal axis represents the number of iterations, and the vertical axis represents the cost $J$.
    - This plot is known as a learning curve.
3. **Learning Curve Analysis**
    
    - Each point on the curve corresponds to the cost $J$ after a certain number of iterations.
    - A well-functioning gradient descent should show a consistently decreasing cost $J$ after each iteration.
    - If $J$ ever increases, it indicates that $\alpha$ may be too large or there could be a bug in the code.
4. **Convergence Indication**
    
    - When the learning curve flattens out, indicating that $J$ is no longer decreasing significantly, gradient descent has converged.
    - The number of iterations required for convergence varies widely between different applications.
5. **Automatic Convergence Test**
    
    - Define a small number $\epsilon$, such as $0.001$ or $10^{-3}$.
    - If the decrease in $J$ is less than $\epsilon$ for one iteration, declare convergence.
    - Choosing the right $\epsilon$ can be challenging; visual inspection of the learning curve is often more reliable.
6. **Practical Insights**
    
    - Creating a learning curve helps monitor the training process and ensure proper convergence.
    - Visual inspection of the learning curve provides early warnings if gradient descent is not functioning correctly.