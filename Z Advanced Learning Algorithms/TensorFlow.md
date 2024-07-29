![[Pasted image 20240710221230.png]]
![[Pasted image 20240710221340.png]]# Summary Notes: Data Representation in NumPy and TensorFlow

## Introduction
- **NumPy and TensorFlow**: Two libraries used for data representation and manipulation in Python.
  - NumPy: Standard library for linear algebra.
  - TensorFlow: Created by Google Brain team for efficient neural network computations.
- **Inconsistencies**: Differences in data representation between NumPy and TensorFlow.

## TensorFlow Data Representation
- Example: Coffee dataset.
- **Double Square Brackets**: Used to define matrices in TensorFlow.

## NumPy Data Representation
- **Vectors and Matrices**:
  - **Matrix Example**: 
    - $2 \times 3$ matrix: Two rows, three columns.
    - Code: `x = np.array([[1, 2, 3], [4, 5, 6]])`
  - **Matrix Example**:
    - $4 \times 2$ matrix: Four rows, two columns.
    - Code: `x = np.array([[1, 2], [3, 4], [5, 6], [7, 8]])`

## Vector Types
- **Row Vector**: 1 row, multiple columns.
  - Example: `x = np.array([[200, 17]])` creates a $1 \times 2$ matrix.
- **Column Vector**: Multiple rows, 1 column.
  - Example: `x = np.array([[200], [17]])` creates a $2 \times 1$ matrix.
- **1D Array**: Linear array without rows or columns.
  - Example: `x = np.array([200, 17])`

## TensorFlow Conventions
- **Matrices over 1D Arrays**: TensorFlow prefers matrices for computational efficiency.
- **Tensor**: Data type in TensorFlow for efficient matrix computations.
  - Example: `a1 = layer1(x)` produces a $1 \times 3$ matrix.
  - Printing: `tf.tensor([0.2, 0.7, 0.3], shape=(1, 3), dtype=float32)`

## Converting Between NumPy and TensorFlow
- **NumPy to TensorFlow**: TensorFlow converts NumPy arrays to tensors for computations.
- **TensorFlow to NumPy**: Use `.numpy()` method.
  - Example: `a1.numpy()` converts TensorFlow tensor `a1` back to a NumPy array.

## Example Workflow
1. Define a NumPy array: `x = np.array([[200, 17]])`.
2. Convert to TensorFlow tensor: `x_tf = tf.convert_to_tensor(x)`.
3. Perform computations in TensorFlow.
4. Convert back to NumPy if needed: `x_np = x_tf.numpy()`.

# TensorFlow Neural Network Lecture Notes

## Building a Neural Network in TensorFlow

### Explicit Forward Propagation
Previously, we manually performed forward propagation by:
1. Initializing the data \( X \)
2. Creating layer 1 and computing \( A_1 \)
3. Creating layer 2 and computing \( A_2 \)

This method involves explicit computation layer by layer.

### Sequential API in TensorFlow
TensorFlow offers a different, simpler way to build neural networks using the `Sequential` API:
1. Create layers (layer 1, layer 2, etc.)
2. Use the `Sequential` function to string layers together into a neural network

```python
import numpy as np
import tensorflow as tf
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense

# Example data
X = np.array([[...], [...], [...], [...]])
Y = np.array([1, 0, 0, 1])

# Creating a Sequential model
model = Sequential([
    Dense(3, activation='sigmoid'),
    Dense(1, activation='sigmoid')
])

# Compiling the model
model.compile(optimizer='adam', loss='binary_crossentropy', metrics=['accuracy'])

# Fitting the model
model.fit(X, Y, epochs=10)

# Predicting with new data
X_new = np.array([[...], [...]])
predictions = model.predict(X_new)
```
### Digit Classification Example

For a digit classification task, the process is similar:

1. Specify layers (layer 1, layer 2, layer 3)
2. Use the `Sequential` function to create the model
3. Store data in a matrix
4. Compile and fit the model
5. Use `model.predict` for inference

```python
# Example for digit classification
model = Sequential([
    Dense(64, activation='relu', input_shape=(784,)),
    Dense(64, activation='relu'),
    Dense(10, activation='softmax')
])

model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics=['accuracy'])

# Assume X_train and Y_train are your training data
model.fit(X_train, Y_train, epochs=10)

# Predicting new data
X_new = np.array([...])
predictions = model.predict(X_new)
```
- Forward propagation: How data moves through the network
- Training: Adjusting weights based on loss
- Inference: Making predictions with new data

$$
A^{[1]} = \sigma(W^{[1]}X + b^{[1]}) \\
A^{[2]} = \sigma(W^{[2]}A^{[1]} + b^{[2]})
$$

Capital refers to a matrix, lower case to  an array
```python
def my_dense(a_in, W, b):
    """
    Computes dense layer
    Args:
      a_in (ndarray (n, )) : Data, 1 example 
      W    (ndarray (n,j)) : Weight matrix, n features per unit, j units
      b    (ndarray (j, )) : bias vector, j units  
    Returns
      a_out (ndarray (j,))  : j units|
    """
    units = W.shape[1]
    a_out = np.zeros(units)
    for j in range(units):               
        w = W[:,j]                                    
        z = np.dot(w, a_in) + b[j]         
        a_out[j] = g(z)               
    return(a_out)
```
```python
def my_sequential(x, W1, b1, W2, b2):
    a1 = my_dense(x,  W1, b1)
    a2 = my_dense(a1, W2, b2)
    return(a2)
```
```python
def my_predict(X, W1, b1, W2, b2):
    m = X.shape[0]
    p = np.zeros((m,1))
    for i in range(m):
        p[i,0] = my_sequential(X[i], W1, b1, W2, b2)
    return(p)
```

[[Vectorization in neural networks]]

`BinaryCrossentropy()` used for binary classification tasks with two classes
epochs =-> number of steps in gradient descent

```python
model.compile(loss=BinaryCrossentropy())
model.fit(X,y,epochs=100)
)
```