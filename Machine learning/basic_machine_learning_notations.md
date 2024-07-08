
![[General Notation.png]]

- NumPy, a popular library for scientific computing
- Matplotlib, a popular library for plotting data
```
import numpy as np
import matplotlib.pyplot as plt

print(f"x_train.shape: {x_train.shape}")
m = x_train.shape[0]
print(f"Number of training examples is: {m}")

scatter() #Method for plotting

# Plot the data points
plt.scatter(x_train, y_train, marker='x', c='r')
# Set the title
plt.title("Housing Prices")
# Set the y-axis label
plt.ylabel('Price (in 1000s of dollars)')
# Set the x-axis label
plt.xlabel('Size (1000 sqft)')
plt.show()
```
for 𝑥(0)𝑥(0), `f_wb = w * x[0] + b`

for 𝑥(1)𝑥(1), `f_wb = w * x[1] + b`

**Note**: The argument description `(ndarray (m,))` describes a Numpy n-dimensional array of shape (m,). `(scalar)` describes an argument without dimensions, just a magnitude.  

**Note**: `np.zero(n)` will<mark style="background: #D2B3FFA6;"> return a one-dimensional numpy array with 𝑛 entries</mark>

```
def compute_model_output(x, w, b):
    """
    Computes the prediction of a linear model
    Args:
      x (ndarray (m,)): Data, m examples 
      w,b (scalar)    : model parameters  
    Returns
      f_wb (ndarray (m,)): model prediction
    """
    m = x.shape[0]
    f_wb = np.zeros(m)
    for i in range(m):
        f_wb[i] = w * x[i] + b
        
    return f_wb
```