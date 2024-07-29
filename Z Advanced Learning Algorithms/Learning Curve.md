# Learning Curves and Diagnosing Bias and Variance

## Learning Curves Overview

- **Purpose:**
  - Understand how a learning algorithm performs as a function of the amount of training data.
  
- **Plotting Learning Curves:**
  - Horizontal Axis: `m_train` (training set size)
  - Vertical Axis: Error (`J_cv` or `J_train`)

### Example: Second-Order Polynomial

- **Cross-Validation Error (J_cv):**
  - Decreases as `m_train` increases.
  
- **Training Error (J_train):**
  - Increases as `m_train` increases.
  - Explanation: With few training examples, it's easier to achieve low error. As the dataset grows, fitting perfectly becomes harder.

### Characteristics of Learning Curves

- **Cross-Validation Error (`J_cv`):**
  - Typically higher than training error.

## High Bias (Underfitting)

- **Example: Linear Function**
- **Training Error (`J_train`):**
  - Increases and plateaus.
  
- **Cross-Validation Error (`J_cv`):**
  - Decreases and plateaus, remaining higher than `J_train`.
  
- **Indicators:**
  - Big gap between human-level performance and `J_train` and `J_cv`.
  - Adding more training data does not help much.

## High Variance (Overfitting)

- **Example: Fourth-Order Polynomial**
- **Training Error (`J_train`):**
  - Increases with more training examples.
  
- **Cross-Validation Error (`J_cv`):**
  - Much higher than `J_train`, indicating overfitting.
  
- **Indicators:**
  - Significant gap between `J_cv` and `J_train`.
  - Adding more training data can help reduce `J_cv`.

## Diagnosing Bias and Variance with Learning Curves

### High Bias

- **Indicators:**
  - `J_train` is high and plateaus.
  - `J_cv` is also high and plateaus.
  - Adding more data does not help significantly.

![[Pasted image 20240716212502.png]]