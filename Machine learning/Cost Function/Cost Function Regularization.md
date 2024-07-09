# Applying Regularization in Machine Learning

In this video, we build on the intuition developed earlier and modify the cost function for our learning algorithm to apply regularization effectively. Let's dive into how this can be achieved.

## Recap: Intuition Behind Regularization

### High Variance and Overfitting

Recall from the previous video that fitting a high-order polynomial can result in overfitting. For instance, a quadratic function fits data well, but a higher-order polynomial creates a curve that overfits.

### Regularization Example

Suppose we want to make certain parameters, \(W_3\) and \(W_4\), really small. Instead of minimizing the original cost function, we modify it by adding terms to penalize \(W_3\) and \(W_4\):
$$
 \text{New Cost Function} = J(\theta) + 1000 \cdot W_3^2 + 1000 \cdot W_4^2 
$$
Choosing a large number (e.g., 1000) ensures \(W_3\) and \(W_4\) are minimized, reducing their impact and avoiding overfitting.

## Generalized Regularization

### Penalizing All Parameters

In practice, you may not know which features are important. Thus, regularization typically penalizes all \(W_j\) parameters to encourage simpler models:
$$
 \text{New Cost Function} = J(\theta) + \lambda \sum_{j=1}^{n} W_j^2 
$$
Here, \(\lambda\) is the regularization parameter.

### Scaling by Training Set Size

By convention, the regularization term is often scaled by \(2m\) (where \(m\) is the training set size):
$$
 \text{Regularized Cost Function} = \frac{1}{2m} \left[ \sum_{i=1}^{m} (h_\theta(x^{(i)}) - y^{(i)})^2 + \lambda \sum_{j=1}^{n} W_j^2 \right] 
$$
This scaling makes it easier to choose a suitable \(\lambda\) and ensures that the chosen \(\lambda\) remains effective even if the training set size changes.

### Excluding Bias Term

By convention, the bias term \(b\) is not penalized. While some implementations may include \(\lambda \cdot b^2\), it typically has little impact on performance.

## Trade-off in Regularization

Regularization balances two goals:
1. **Minimize training error:** Fit the training data well by minimizing the mean squared error.
2. **Keep parameters small:** Reduce the magnitude of \(W_j\) parameters to prevent overfitting.

The choice of \(\lambda\) determines the trade-off between these goals.

## Impact of \(\lambda\) on Model Performance

### Extreme Values of \(\lambda\)

- **\(\lambda = 0\):** No regularization; the model may overfit.
- **\(\lambda\) very large (e.g., \(10^{10}\)):** Strong regularization; parameters \(W_j\) approach 0, leading to underfitting (model fits a horizontal line).

### Optimal \(\lambda\)

The ideal \(\lambda\) is somewhere in between, balancing the fit to the training data and the regularization term.

## Visualizing the Impact

### Overfitting (\(\lambda = 0\))

![[Pasted image 20240709142612.png]]

### Underfitting (\(\lambda\) very large)

![[Pasted image 20240709142657.png]]

```
def compute_cost_linear_reg(X, y, w, b, lambda_ = 1):
    """
    Computes the cost over all examples
    Args:
      X (ndarray (m,n): Data, m examples with n features
      y (ndarray (m,)): target values
      w (ndarray (n,)): model parameters  
      b (scalar)      : model parameter
      lambda_ (scalar): Controls amount of regularization
    Returns:
      total_cost (scalar):  cost 
    """

    m  = X.shape[0]
    n  = len(w)
    cost = 0.
    for i in range(m):
        f_wb_i = np.dot(X[i], w) + b                                   #(n,)(n,)=scalar, see np.dot
        cost = cost + (f_wb_i - y[i])**2                               #scalar             
    cost = cost / (2 * m)                                              #scalar  
 
    reg_cost = 0
    for j in range(n):
        reg_cost += (w[j]**2)                                          #scalar
    reg_cost = (lambda_/(2*m)) * reg_cost                              #scalar
    
    total_cost = cost + reg_cost                                       #scalar
    return total_cost      
```

```
def compute_cost_logistic_reg(X, y, w, b, lambda_ = 1):
    """
    Computes the cost over all examples
    Args:
    Args:
      X (ndarray (m,n): Data, m examples with n features
      y (ndarray (m,)): target values
      w (ndarray (n,)): model parameters  
      b (scalar)      : model parameter
      lambda_ (scalar): Controls amount of regularization
    Returns:
      total_cost (scalar):  cost 
    """

    m,n  = X.shape
    cost = 0.
    for i in range(m):
        z_i = np.dot(X[i], w) + b                                      #(n,)(n,)=scalar, see np.dot
        f_wb_i = sigmoid(z_i)                                          #scalar
        cost +=  -y[i]*np.log(f_wb_i) - (1-y[i])*np.log(1-f_wb_i)      #scalar
             
    cost = cost/m                                                      #scalar

    reg_cost = 0
    for j in range(n):
        reg_cost += (w[j]**2)                                          #scalar
    reg_cost = (lambda_/(2*m)) * reg_cost                              #scalar
    
    total_cost = cost + reg_cost                                       #scalar
    return total_cost
```

[[Computing the Gradient with regularization]]
