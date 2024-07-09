#### Examples of Classification Problems

- **Spam Detection:** Is an email spam? (yes/no)
- **Fraud Detection:** Is a transaction fraudulent? (yes/no)
- **Tumor Classification:** Is a tumor malignant or benign?

In these binary classification problems, the output is either 0 (negative) or 1 (positive).

#### Why Linear Regression Fails for Classification

Consider classifying tumors as malignant or benign based on size:

1. **Initial Training Set:**
    
    - Plot tumor size on the horizontal axis and label yyy (0 or 1) on the vertical axis.
    - Fit a straight line using linear regression.
    - Use a threshold (e.g., 0.5) to classify tumors.
2. **Problem with an Outlier:**
    
    - Adding an outlier shifts the best-fit line, changing the decision boundary and leading to incorrect classifications.

Linear regression fails because outliers distort the decision boundary, resulting in poor performance.

#### Logistic Regression
[[Logistic Regression]]

Logistic regression ensures the output is between 0 and 1, making it suitable for binary classification. Despite its name, logistic regression is used for classification.

In the next video, you'll learn more about the decision boundary and logistic regression. An optional lab will let you experiment with linear regression for classification, highlighting its limitations and the need for logistic regression