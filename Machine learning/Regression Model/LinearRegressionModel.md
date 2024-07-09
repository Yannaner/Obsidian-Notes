#Machinelearning 
**Linear Regression Model:**

- Linear regression fits a straight line to the data.
- **Example:** Predicting house prices based on the size of the house.
    - **Dataset:** Sizes and prices of houses in Portland.
    - **Graph:**
        - Horizontal axis: Size of the house (square feet).
        - Vertical axis: Price of the house (thousands of dollars).
**Notation and Terminology:**

- **Training Set:** Dataset used to train the model.
- **Input Variable (xxx):** Feature or input feature (e.g., size of the house).
- **Output Variable (yyy):** Target variable (e.g., price of the house).
- **Training Example:** Each row in the dataset (e.g., (2104, 400)).
- **Number of Training Examples (mmm):** Total number of examples (e.g., 47).

**Standard Notation:**

- $x^i$: Input for the iii-th training example.
- $y^i$: Output for the iii-th training example.
- Superscript iii indicates the iii-th example, not exponentiation.
##### Process:
**Supervised Learning Overview:**

- **Input:** A dataset containing both input features xxx (e.g., size of the house) and output targets $y$ (e.g., price of the house).
- **Output:** A function $f$ that can predict $\hat{y}$ for a new input xxx.

	The function $f$ is used to make predictions $\hat{y}$​ for new inputs.
**Prediction ($\hat{y}$):**
    - $\hat{y}$ (y-hat) represents the estimated value of $y$.
    - $\hat{y}$ is the model's prediction, which may or may not match the actual true value $y$.

**Linear Regression Model:**

- **Function Representation:**
    - $f(x) = wx + b$, where:
        - $w$ (weight) and $b$ (bias) are parameters that determine the prediction $\hat{y}$ based on input $x$.
        - $f(x)$ or $f_{w,b}(x)$ is the linear function used to make predictions.
- **Plotting the Training Set:**
    - **Graph:** Input feature $x$ on the horizontal axis, output target $y$ on the vertical axis.
    - The algorithm fits a straight line to the data, representing the linear function $f(x)$.

**Why Linear Function?**

- **Simplicity and Foundation:**
    - Linear functions (straight lines) are simple and easy to work with.
    - They serve as a foundation for understanding more complex non-linear functions.
- **Linear Regression with One Variable:**
    - Also called **univariate linear regression**.
    - "Univariate" means there's a single input variable (feature) $x$.

**Cost Function:**

- **Purpose:**
    - Helps evaluate how well the model is performing by measuring the difference between the predicted values $\hat{y}$ and the actual values $y$.
- **Importance:**
    - Essential for training both simple and complex AI models.

Basic Model training notations: [[basic_machine_learning_notations]]