# Machine Learning Workflow and Diagnosing Bias and Variance

## Typical Workflow

1. **Initial Steps:**
   - Start with an idea.
   - Train the model.
   - Often, the initial model doesn't perform as well as desired.

2. **Key Process:**
   - Determine the next steps to improve performance.
   - Assess bias and variance to guide improvements.

## Understanding Bias and Variance

### <mark style="background: #D2B3FFA6;">High Bias (Underfitting)</mark>

- **Example:**
  - Straight line fitting to dataset.
  - **Characteristics:**
    - J_train (training error) is high.
    - J_cv (cross-validation error) is also high.
  - **Indicator:**
    - Poor performance on training set.
    - High J_train.

### <mark style="background: #D2B3FFA6;">High Variance (Overfitting)</mark>

- **Example:**
  - Fourth-order polynomial fitting to dataset.
  - **Characteristics:**
    - J_train is low.
    - J_cv is high.
  - **Indicator:**
    - Good performance on training set.
    - Poor performance on unseen examples (high J_cv).

### Balanced Model

- **Example:**
  - Quadratic polynomial fitting to dataset.
  - **Characteristics:**
    - Both J_train and J_cv are low.
  - **Indicator:**
    - Good performance on both training and cross-validation sets.

## Visualizing Bias and Variance

### Plotting J_train and J_cv

- **Horizontal Axis:**
  - Degree of polynomial (d).
  - d = 1: Low degree (underfitting).
  - d = 4+: High degree (overfitting).

- **J_train (Training Error):**
  - Decreases as the degree of the polynomial increases.
  
- **J_cv (Cross-validation Error):**
  - High for both low and high degrees.
  - Low for intermediate degrees (optimal fit).
![[Pasted image 20240716164727.png]]

## Diagnosing Bias and Variance

### Key Indicators

- **High Bias:**
  - J_train is high.
  - J_cv is also high.
  - Indicates underfitting.

- **High Variance:**
  - J_train is low.
  - J_cv is much higher than J_train.
  - Indicates overfitting.

- **Balanced Model:**
  - Both J_train and J_cv are low.
  - Indicates good fit.

### Simultaneous High Bias and High Variance

- **Possible but rare:**
  - High J_train and even higher J_cv.
  - Can occur in complex models (e.g., neural networks).

## Conclusion

- **Diagnosing Bias and Variance:**
  - Critical for improving model performance.
  - High bias: Focus on improving training accuracy.
  - High variance: Focus on improving generalization.

- **Next Steps:**
  - Understand regularization and its effects on bias and variance.

Diagnosing the r[[Computing the Gradient with regularization]] lamba value

![[Pasted image 20240716172600.png]]
[[Learning Curve]]
![[Pasted image 20240716212502.png]]

![[Pasted image 20240716215532.png]]
[[Error Analysis]]

![[Pasted image 20240718141142.png]]![[Pasted image 20240718142013.png]]