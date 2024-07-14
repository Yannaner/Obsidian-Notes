# Neural Network: Forward Propagation Algorithm

: Handwritten Digit Recognition
For simplicity, we are going to distinguish between the handwritten digits zero and one. So it's just a binary classification problem where we're going to input an image and classify, is this the digit zero or the digit one?

## Input Image
- **Image**: 8x8 matrix (64 pixel intensity values)
  - **255**: Bright white pixel
  - **0**: Black pixel
  - Different numbers are different shades of gray

## Neural Network Architecture
- **Input Layer**: 64 input features (pixel values)
- **First Hidden Layer**: 25 neurons (units)
- **Second Hidden Layer**: 15 neurons (units)
- **Output Layer**: 1 neuron (probability of digit 1)

## Sequence of Computations
### Step 1: Compute $a^{[1]}$
- **From $X$ to $a^{[1]}$**
- **Computation**: $a^{[1]} = g(W^{[1]} \cdot X + b^{[1]})$
- **Parameters**: $W_1^{[1]}, W_2^{[1]}, \ldots, W_{25}^{[1]}$ $b_1^{[1]}, b_2^{[1]}, \ldots, b_{25}^{[1]}$
- **Output**: $a^{[1]}$ (25 numbers)

### Step 2: Compute $a^{[2]}$
- **From $a^{[1]}$ to $a^{[2]}$**
- **Computation**: $a^{[2]} = g(W^{[2]} \cdot a^{[1]} + b^{[2]})$
- **Parameters**: $W_1^{[2]}, W_2^{[2]}, \ldots, W_{15}^{[2]}$ $b_1^{[2]}, b_2^{[2]}, \ldots, b_{15}^{[2]}$
- **Output**: $a^{[2]}$ (15 numbers)

### Step 3: Compute $a^{[3]}$
- **From $a^{[2]}$ to $a^{[3]}$**
- **Computation**: $a^{[3]} = g(W^{[3]} \cdot a^{[2]} + b^{[3]})$
- **Parameters**: $W_1^{[3]}$ $b_1^{[3]}$
- **Output**: $a^{[3]}$ (scalar)

### Optional Step: Binary Classification
- **Threshold $a^{[3]}$ at 0.5**: $a^{[3]} \geq 0.5 \Rightarrow$ Digit 1, otherwise Digit 0

## Notation
- **$f(X)$**: Function computed by the neural network as a function of $X$
- **Forward Propagation**: Propagating the activations of the neurons from left to right
