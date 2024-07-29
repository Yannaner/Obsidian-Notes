# Model Selection in Machine Learning

## Evaluating Models
- **Training Error**: Measures how well the model fits the training data.
- **Test Error**: Evaluates performance on new, unseen data. This gives a better idea of how the model will generalize.

## Problem with Training and Test Errors
- Training error is often too optimistic.
- Test error alone can also be misleading if used to choose model parameters.

## Example: Polynomial Regression
Consider fitting polynomial models of different degrees (d):
- **1st Order Polynomial (d=1)**: Linear model.
- **2nd Order Polynomial (d=2)**: Quadratic model.
- **3rd Order Polynomial (d=3)**: Cubic model.
- ...
- **10th Order Polynomial (d=10)**: High-degree polynomial.

For each model, we calculate:
- Parameters \( w \) and \( b \).
- Test error \( J_{test}(w, b) \).

## Flawed Procedure
If we choose the model with the lowest test error, \( J_{test} \), the chosen model might be overly optimistic.

## Improved Procedure: Cross-Validation
1. **Split Data into Three Sets**:
   - **Training Set**: Used to fit model parameters.
   - **Cross-Validation Set**(dev set): Used to choose the model.
   - **Test Set**: Used to estimate generalization error.

Example Split:
- **Training Set**: 60% of the data.
- **Cross-Validation Set**: 20% of the data.
- **Test Set**: 20% of the data.

2. **Compute Errors**:
   - **Training Error**: On the training set.
   - **Cross-Validation Error**: On the cross-validation set.
   - **Test Error**: On the test set.

## Model Selection Process
1. Fit models to the training set.
2. Evaluate models on the cross-validation set.
3. Choose the model with the<mark style="background: #D2B3FFA6;"> lowest cross-validation error.</mark>
4. Estimate the chosen model's performance on the test set.

## Example: Polynomial Regression
For each polynomial degree \( d \):
1. Fit parameters \( w^d \), \( b^d \).
2. Compute cross-validation error \( J_{cv}(w^d, b^d) \).
3. Choose the model with the lowest \( J_{cv} \).

## Estimating Generalization Error
After selecting the best model using the cross-validation set, use the test set to get an unbiased estimate of the generalization error.

## Application to Neural Networks
- Consider different network architectures (e.g., small, medium, large).
- Fit each model and evaluate using cross-validation error \( J_{cv} \).
- Choose the architecture with the lowest cross-validation error.
- Report generalization error using the test set.

## Best Practices
- **Training and Cross-Validation**: Use these sets to make all decisions about the model.
- **Test Set**: Use only for final evaluation to ensure an unbiased estimate of performance.

## Conclusion
Using cross-validation allows you to choose the best model and get a fair estimate of its performance on new data. This procedure helps avoid overly optimistic estimates and ensures better generalization.

```python
for model in models_bc:
    
    # Setup the loss and optimizer
    model.compile(
    loss=tf.keras.losses.BinaryCrossentropy(from_logits=True),
    optimizer=tf.keras.optimizers.Adam(learning_rate=0.01),
    )

    print(f"Training {model.name}...")

    # Train the model
    model.fit(
        x_bc_train_scaled, y_bc_train,
        epochs=200,
        verbose=0
    )
    
    print("Done!\n")
    
    # Set the threshold for classification
    threshold = 0.5
    
    # Record the fraction of misclassified examples for the training set
    yhat = model.predict(x_bc_train_scaled)
    yhat = tf.math.sigmoid(yhat)
    yhat = np.where(yhat >= threshold, 1, 0)
    train_error = np.mean(yhat != y_bc_train)
    nn_train_error.append(train_error)

    # Record the fraction of misclassified examples for the cross validation set
    yhat = model.predict(x_bc_cv_scaled)
    yhat = tf.math.sigmoid(yhat)
    yhat = np.where(yhat >= threshold, 1, 0)
    cv_error = np.mean(yhat != y_bc_cv)
    nn_cv_error.append(cv_error)

# Print the result
for model_num in range(len(nn_train_error)):
    print(
        f"Model {model_num+1}: Training Set Classification Error: {nn_train_error[model_num]:.5f}, " +
        f"CV Set Classification Error: {nn_cv_error[model_num]:.5f}"
        )
```