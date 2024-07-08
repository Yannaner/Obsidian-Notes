#### Overview

In this lecture, we reviewed multiple linear regression, introduced vectorization for the parameters, and implemented gradient descent using vector notation. Additionally, we touched on an alternative method called the normal equation.

#### Key Points

1. **Multiple Linear Regression Recap**
    
    - Parameters $w_1$ to $w_n$ and bias $b$ are considered.
    - Collect parameters $w_1$ to $w_n$ into a vector $\mathbf{w}$.
    - Model representation: $f_{\mathbf{w}, b}(\mathbf{x}) = \mathbf{w} \cdot \mathbf{x} + b$.
2. **Cost Function**
    
    - Original form: $J(w_1, w_2, ..., w_n, b)$.
    - Vector form: $J(\mathbf{w}, b)$.
3. **Gradient Descent for Multiple Linear Regression**
    
    - Update rule for each parameter $$w_j = w_j - \alpha \frac{\partial J}{\partial w_j}
$$
    - Update rule for bias $b$:$$b = b - \alpha \frac{\partial J}{\partial b}
$$
- ![[Multiple Linear regression gradient descent.png]]
1. **Vectorized Gradient Descent**
    
    - Update all $w_j$ parameters simultaneously.
    - Handle multiple features (dimensions).
5. **Normal Equation Method**
    
    - An alternative to gradient descent.
    - Directly solves for $\mathbf{w}$ and $b$ using linear algebra.
    - Advantages:
        - No iterative process.
    - Disadvantages:
        - Not generalized to other algorithms like logistic regression or neural networks.
        - Slower for large feature sets.
        - Rarely implemented manually by practitioners but may be used in some machine learning libraries.

[[General Notation.png]]
