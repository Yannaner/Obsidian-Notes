#### Tumor Classification Example

- **Labels:**
    - $1$ (yes) for malignant tumors (positive class).
    - $0$ (no) for benign tumors (negative class).
- **Graph:**
    - Horizontal axis: tumor size.
    - Vertical axis: values of $0$ and $1$.

#### Why Linear Regression Fails

- **Linear Regression Fit:**
    - Predicts values between $0$ and $1$, but can also predict outside this range.
    - Adding an outlier can shift the best-fit line, changing the decision boundary and leading to incorrect classifications.

#### Logistic Regression

- **Curve:**
    - Logistic regression fits an S-shaped curve to the data.
    - Outputs a value between $0$ and $1$, interpreted as a probability.
- **Sigmoid Function:**
    - **Formula:** $g(z) = \frac{1}{1 + e^{-z}}$
    - **Range:** Outputs values between $0$ and $1$.
    - **Behavior:**
        - $g(z) \approx 1$ when $z$ is large.
        - $g(z) \approx 0$ when $z$ is a large negative number.
        - $g(0) = 0.5$

#### Logistic Regression Model

- **Model Equation:**
    
    - **Linear Function:** $z = w \cdot x + b$
    - **Logistic Function:** $f(x) = g(z) = g(w \cdot x + b)$
- **Output Interpretation:**
    
    - The model outputs the probability that $ y = 1 $ given input $x$.
    - Example: If $x$ (tumor size) leads to an output of $0.7$, there's a $70%$ chance the tumor is malignant.
    - The probability that $ y = 0 $ is $1 - 0.7 = 0.3$.

#### Mathematical Notation

- **Probability Notation:**
    - $f(x) = P(y = 1 \mid x; w, b)$
    - $w$ and $b$ are parameters of the model.

[[Decision Boundary in Logistic Regression]]