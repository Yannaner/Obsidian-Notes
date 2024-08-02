# Convolutional Neural Networks (CNNs)

## Dense Layers Recap
In dense layers, every neuron gets input from all the activations in the previous layer. This can build powerful learning algorithms.

## Convolutional Layers
Convolutional layers are different. They allow each neuron to look at only a small part of the input, not the whole thing. Let's see how this works.

### Example: Handwritten Digit Recognition
- **Input**: A handwritten digit, like '9'.
- **Dense Layer**: Every neuron looks at all the pixels.
- **Convolutional Layer**: Each neuron looks at a small rectangular region of the image.

#### Visualization
- **First Neuron**: Looks at a small region.
- **Second Neuron**: Looks at a different small region, and so on.

### Benefits of Convolutional Layers
1. **Faster Computation**: Since each neuron looks at fewer pixels.
2. **Less Training Data Needed**: Helps prevent overfitting.

## EKG Signal Example
Let's consider a 1D input like an EKG (electrocardiogram) signal to diagnose heart conditions.

1. **Input**: EKG signal with 100 data points (\(X_1, X_2, \ldots, X_{100}\)).
2. **First Hidden Layer**: Each neuron looks at a small window of inputs.
   - **First Neuron**: Looks at \(X_1\) to \(X_{20}\).
   - **Second Neuron**: Looks at \(X_{11}\) to \(X_{30}\), and so on.
3. **Second Hidden Layer**: Each neuron looks at a small window of the previous layer's activations.
   - **First Neuron**: Looks at activations \(A_1\) to \(A_5\).
   - **Second Neuron**: Looks at \(A_3\) to \(A_7\), and so on.

### Final Layer
A sigmoid unit can take inputs from the last convolutional layer to make a binary classification.

## Architectural Choices
In convolutional layers, you decide:
- **Window Size**: How many inputs a neuron should look at.
- **Number of Neurons**: How many neurons each layer should have.

Choosing these wisely can create effective neural networks.

## Conclusion
Convolutional layers are powerful tools that can improve neural networks. They help make faster computations and need less training data. Understanding these layers opens up new possibilities for building advanced models.

### Future Directions
Research continues to develop new types of layers, like transformers and LSTMs. Combining these layers can create even more powerful neural networks.

Congratulations on completing this material! Next week, we'll cover practical advice for building machine learning systems to help you become more effective in this field.


