#Machinelearning
**Objective:** The primary goal of linear regression is to find values for the parameters $w$ and $b$ that make the predictions $\hat{y}$ as close as possible to the actual target values $y$. To achieve this, we use a cost function that quantifies how well the model is performing.

**Training Set:**

- Input features: $x$
- Output targets: $y$
- Model: $f_{w,b}(x) = wx + b$
- Parameters: $w$ (weight), $b$ (bias)

**Parameters of the Model:**

- **$w$ and $b$:**
    - $w$: Slope of the line.
    - $b$: y-intercept, where the line crosses the y-axis.
    - The values of $w$ and $b$ determine the position and angle of the line on the graph.

**Impact of Parameters:**

- When $w = 0$ and $b = 1.5$, $f(x)$ is a horizontal line at $y = 1.5$.
- When $w = 0.5$ and $b = 0$, $f(x)$ is a line with a slope of 0.5 passing through the origin.
- When $w = 0.5$ and $b = 1$, $f(x)$ is a line with a slope of 0.5 and y-intercept at 1.

**Visualizing Linear Regression:**

- The goal is to fit a line to the training data such that the line is as close as possible to the data points.
- Notation for a training example: $(x^{(i)}, y^{(i)})$
- Prediction for a given input $x^{(i)}$: $\hat{y}^{(i)} = f_{w,b}(x^{(i)}) = wx^{(i)} + b$

**Constructing the Cost Function:**

1. **Error Calculation:**
    
    - Error for a single training example: $\text{error} = \hat{y}^{(i)} - y^{(i)}$
    - Squared error for a single example: $(\hat{y}^{(i)} - y^{(i)})^2$
2. **Sum of Squared Errors:**
    
    - Sum over all training examples: $\sum_{i=1}^{m} (\hat{y}^{(i)} - y^{(i)})^2$
3. **Mean Squared Error (MSE):**
    
    - To average the squared error, divide by the
    - number of examples $m$: $\frac{1}{m} \sum_{i=1}^{m} (\hat{y}^{(i)} - y^{(i)})^2$
1. **Final Cost Function:**
    
    - By convention, divide by $2m$ for simplicity in later calculations: $J(w,b) = \frac{1}{2m} \sum_{i=1}^{m} (\hat{y}^{(i)} - y^{(i)})^2$
    - This is called the **squared error cost function**.

**Mathematical Representation:**

- $\hat{y}^{(i)} = f(x^{(i)}) = wx^{(i)} + b$
- Cost function $J(w,b)$: $J(w,b) = \frac{1}{2m} \sum_{i=1}^{m} (f_{w,b}(x^{(i)}) - y^{(i)})^2$

**Intuition:**

- A lower value of $J(w,b)$ indicates a better fit of the model to the training data.
- The aim is to find $w$ and $b$ that minimize $J(w,b)$, leading to more accurate predictions.
[[Cost Function Intuition]]
[[Cost Function for Logistic Regression]]