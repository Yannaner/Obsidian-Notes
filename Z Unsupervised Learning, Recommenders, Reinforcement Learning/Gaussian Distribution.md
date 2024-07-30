Also called as the normal distribution

# Anomaly Detection Algorithm Using Gaussian Distribution

## Key Concepts
- **Training Set**: $x_1, x_2, \ldots, x_m$ where each example $x$ has $n$ features.
- **Density Estimation**: Estimate the probability $p(x)$ of a feature vector $x$.

## Steps to Build Anomaly Detection System

1. **Modeling the Probability**:
   - Each feature vector $x$ is represented as $(x_1, x_2, \ldots, x_n)$.
   - Model $p(x)$ as the product of the probabilities of individual features: 
     $$
     p(x) = p(x_1) \cdot p(x_2) \cdot \ldots \cdot p(x_n)
     $$

2. **Parameter Estimation**:
   - For each feature $x_j$:
     - Estimate the mean $\mu_j$ and variance $\sigma_j^2$.
     - Use these parameters to model the Gaussian distribution for each feature.
   
3. **Probability Calculation**:
   - Calculate $p(x)$ for a new example $x$ using the formula:
     $$
     p(x) = \prod_{j=1}^{n} p(x_j; \mu_j, \sigma_j^2)
     $$
   - Where:
     $$
     p(x_j; \mu_j, \sigma_j^2) = \frac{1}{\sqrt{2\pi\sigma_j^2}} \exp\left(-\frac{(x_j - \mu_j)^2}{2\sigma_j^2}\right)
     $$

4. **Anomaly Detection**:
   - Compare $p(x)$ to a threshold $\epsilon$:
     - If $p(x) < \epsilon$, flag it as an anomaly.

## Example Workflow

1. **Choose Features**: Select features $x_j$ indicative of anomalies.
2. **Fit Parameters**:
   - Compute $\mu_j$ as the mean of the feature $x_j$ across the training set.
   - Compute $\sigma_j^2$ as the variance of the feature $x_j$ across the training set.
3. **Compute Probability for New Example**:
   - For a new example $x_{\text{test}}$:
     $$
     p(x_{\text{test}}) = \prod_{j=1}^{n} p(x_{\text{test}, j}; \mu_j, \sigma_j^2)
     $$
   - Compare $p(x_{\text{test}})$ with $\epsilon$.

## Practical Example

- **Dataset with Features $x_1$ and $x_2$**:
  - Compute means: $\mu_1 = 5$, $\mu_2 = 3$.
  - Compute variances: $\sigma_1^2 = 4$, $\sigma_2^2 = 1$.
  - Model Gaussian distributions for each feature.

- **Test Examples**:
  - For $x_{\text{test1}}$, calculate $p(x_{\text{test1}})$.
    - If $p(x_{\text{test1}}) = 0.4$ and $\epsilon = 0.02$, it is not an anomaly.
  - For $x_{\text{test2}}$, calculate $p(x_{\text{test2}})$.
    - If $p(x_{\text{test2}}) = 0.0021$, it is an anomaly.

## Conclusion

- **Anomaly Detection**: Useful for identifying unusual patterns in data.
- **Gaussian Distribution**: Effective for modeling feature distributions.
- **Parameter Selection**: Critical for accurate anomaly detection.

# Real-number evaluation

# Practical Tips for Developing an Anomaly Detection System

When developing an anomaly detection system, it is crucial to have a method for evaluating the system as it evolves. This will help in making informed decisions and iteratively improving the system. Here are some practical tips to achieve this:

## Evaluation During Development

1. **Importance of Evaluation**:
    - Evaluate the learning algorithm regularly to decide on changes to features, parameter values (like epsilon), etc.
    - A method to quickly compute a real number evaluation will guide these decisions.

2. **Labeled Data**:
    - Although anomaly detection often involves unlabeled data, having a small amount of labeled data (both normal and anomalous examples) is beneficial.
    - Label normal examples as \( y = 0 \) and anomalous examples as \( y = 1 \).

## Cross-Validation and Test Sets

1. **Training Set**:
    - Use the majority of normal examples to fit the model.
    - It’s okay if a few anomalous examples slip into this set.

2. **Cross-Validation and Test Sets**:
    - Create cross-validation and test sets containing both normal and anomalous examples.
    - Use these sets to tune parameters like epsilon and evaluate the algorithm’s performance.

## Example Workflow

1. **Data Collection**:
    - Suppose you have data from 10,000 normal engines and 20 anomalous engines.
    - Split this data into training, cross-validation, and test sets.

2. **Dataset Splitting**:
    - Training Set: 6,000 normal engines.
    - Cross-Validation Set: 2,000 normal engines and 10 anomalous engines.
    - Test Set: 2,000 normal engines and 10 anomalous engines.

3. **Training**:
    - Train the algorithm on the training set to fit Gaussian distributions.

4. **Cross-Validation**:
    - Tune epsilon using the cross-validation set to detect anomalies without flagging too many normal engines.

5. **Testing**:
    - Evaluate the tuned algorithm on the test set to measure its effectiveness.

## Handling Small Anomaly Counts

1. **Alternative Approach**:
    - If anomalies are very few, combine the remaining normal examples and all anomalies into a single cross-validation set.
    - Train on the training set and validate on the combined set.

2. **Risk of Overfitting**:
    - Without a separate test set, there is a higher risk of overfitting to the cross-validation set.
    - Be cautious about the algorithm's expected performance on future data.

## Evaluating the Algorithm

1. **Model Fitting**:
    - Fit \( p(x) \) on the training set.
    - Compute \( p(x) \) for each example in the cross-validation or test set.
    - Predict \( y = 1 \) (anomalous) if \( p(x) < \epsilon \) and \( y = 0 \) (normal) otherwise.

2. **Performance Metrics**:
    - Assess how well the algorithm's predictions match the labels in the cross-validation or test set.
    - Use metrics like true positive, false positive, false negative, and true negative rates.
    - Consider precision, recall, and F1 score, especially for skewed data distributions.

## Summary

- Regular evaluation during development is crucial for iterative improvement.
- Having a small number of labeled anomalies aids in effective tuning and evaluation.
- Consider using alternative approaches for evaluation when anomalies are scarce.
- Use appropriate performance metrics to gauge the algorithm's effectiveness.