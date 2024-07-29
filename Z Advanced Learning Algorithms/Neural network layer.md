# Neural Network Basics

## Demand Prediction Example

### Inputs and Outputs
- **Input Features**: 4 features
- **Hidden Layer**: 3 neurons
- **Output Layer**: 1 neuron

### Hidden Layer Computation
1. **First Neuron**
   - Parameters: `w_1`, `b_1`
   - Activation: `a_1 = g(w_1 * x + b_1)`
   - Example Activation: `0.3`
   
2. **Second Neuron**
   - Parameters: `w_2`, `b_2`
   - Activation: `a_2 = g(w_2 * x + b_2)`
   - Example Activation: `0.7`
   
3. **Third Neuron**
   - Parameters: `w_3`, `b_3`
   - Activation: `a_3 = g(w_3 * x + b_3)`
   - Example Activation: `0.2`

### Output Layer Computation
- **Input**: Activation values from the hidden layer: `[0.3, 0.7, 0.2]`
- **Single Neuron Computation**:
  - Parameters: `w_1`, `b_1`
  - Activation: `a_2 = g(w_1 * a_1 + b_1)`
  - Example Activation: `0.84`

### Thresholding for Binary Prediction
- If `a_2 > 0.5`, predict `y_hat = 1`
- If `a_2 <= 0.5`, predict `y_hat = 0`

## Notation and Layers
- **Layer Indexing**:
  - Input Layer: `Layer 0`
  - First Hidden Layer: `Layer 1`
  - Output Layer: `Layer 2`

- **Parameter Notation**:
  - `w^[1]`, `b^[1]`: Parameters for the first hidden layer
  - `w^[2]`, `b^[2]`: Parameters for the output layer

- **Activation Notation**:
  - `a^[1]`: Activation values for the first hidden layer
  - `a^[2]`: Activation value for the output layer

### Final Prediction
- The final prediction, `y_hat`, is either a probability or a binary value based on thresholding.
# Building a More Complex Neural Network

## Introduction
- Building on the basic neural network layer to create a more complex network.
- Example: Neural network with 4 layers (excluding the input layer, Layer 0).

## Layer Notation
- **Layers**:
  - Layer 0: Input Layer
  - Layer 1, 2, 3: Hidden Layers
  - Layer 4: Output Layer
- Convention: Neural network with 4 layers refers to 3 hidden layers and 1 output layer.

## Computation in Layer 3
- **Inputs**: Vector `a^[2]` (output of Layer 2)
- **Outputs**: Vector `a^[3]`

### Neuron Computation in Layer 3
1. **First Neuron**:
   - Parameters: `w^[3]_1`, `b^[3]_1`
   - Activation: `a^[3]_1 = sigmoid(w^[3]_1 * a^[2] + b^[3]_1)`

2. **Second Neuron**:
   - Parameters: `w^[3]_2`, `b^[3]_2`
   - Activation: `a^[3]_2 = sigmoid(w^[3]_2 * a^[2] + b^[3]_2)`

3. **Third Neuron**:
   - Parameters: `w^[3]_3`, `b^[3]_3`
   - Activation: `a^[3]_3 = sigmoid(w^[3]_3 * a^[2] + b^[3]_3)`

- **Output Vector**: `[a^[3]_1, a^[3]_2, a^[3]_3]`

### Notation
- Superscripts denote layer numbers.
- Subscripts denote neuron numbers within a layer.
- Example: `w^[3]_1` is the parameter for the first neuron in Layer 3.

## General Form of Neuron Computation
- **Activation of Layer l, Neuron j**:
  - `a^[l]_j = sigmoid(w^[l]_j * a^[l-1] + b^[l]_j)`
  - `w^[l]_j`: Weights for neuron j in layer l
  - `a^[l-1]`: Activations from the previous layer
  - `b^[l]_j`: Bias for neuron j in layer l

### Activation Function
- Function `g` (sigmoid in this context) is called the **activation function**.
- **Activation Function**: Outputs activation values from the neurons.

## Consistent Notation
- Input vector `X` is also denoted as `a^[0]`.
- For the first layer (Layer 1):
  - `a^[1] = sigmoid(w^[1] * a^[0] + b^[1])`
  - `a^[0]` is the input feature vector `X`.
[[Inferences]]

