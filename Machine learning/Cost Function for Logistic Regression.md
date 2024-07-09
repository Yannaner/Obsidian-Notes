# Cost Function for Logistic Regression

The cost function measures how well a set of parameters fits the training data and guides the selection of better parameters.

## Squared Error Cost Function in Logistic Regression

Using the squared error cost function, the cost function for logistic regression is non-convex, making gradient descent unreliable due to multiple local minima.

## Defining a New Cost Function

We need a different cost function to ensure convexity for logistic regression. Let's redefine the cost function \(J(w, b)\).

- **Training Set:**
    - \(m\) denotes the number of training examples.
    - Each example has \(n\) features, \(X_1, X_2, \ldots, X_n\).
    - Target label \(y\) takes on values 0 or 1.
    - Logistic regression model: \(f(x) = \frac{1}{1 + e^{-(w \cdot x + b)}}\).

- **Linear Regression Cost Function:**
    $$
    J(w, b) = \frac{1}{2m} \sum_{i=1}^{m} (f(x^{(i)}) - y^{(i)})^2
    $$

    - For logistic regression, \(f(x) = \frac{1}{1 + e^{-(w \cdot x + b)}}\), resulting in a non-convex cost function.

- **New Cost Function:**
    - Loss function \(L(f(x), y)\):
        $$
        L(f(x), y) = 
        \begin{cases} 
        -\log(f(x)) & \text{if } y = 1 \\
        -\log(1 - f(x)) & \text{if } y = 0 
        \end{cases}
        $$
    - Overall cost function \(J(w, b)\):
        $$
        J(w, b) = \frac{1}{m} \sum_{i=1}^{m} L(f(x^{(i)}), y^{(i)})
        $$

## Intuition Behind the Loss Function

- **Case \(y = 1\):**
    - Loss: \(-\log(f)\).
    - If \(f \approx 1\), loss is close to 0.
    - If \(f \approx 0.5\), moderate loss.
    - If \(f \approx 0.1\), high loss.

    - **Plot of \(-\log(f)\):**
        ![[Pasted image 20240709124530.png]]

- **Case \(y = 0\):**
    - Loss: \(-\log(1 - f)\).
    - If \(f \approx 0\), loss is close to 0.
    - If \(f \approx 0.5\), moderate loss.
    - If \(f \approx 1\), very high loss.

    - **Plot of \(-\log(1 - f)\):**
        ![[Pasted image 20240709124509.png]]

## Convexity of the New Cost Function

- **Convex Cost Function:**
    - The new cost function is convex, allowing reliable gradient descent to find the global minimum.

    - **Surface Plot of Convex Cost Function:**
        ![[Pasted image 20240709124728.png]]

![[Pasted image 20240709125012.png]]

**Loss** is a measure of the difference of a single example to its target value while the  
**Cost** is a measure of the losses over the training set