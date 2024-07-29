- **Early Motivation**:
    
    - Neural networks were initially invented to mimic how the human brain learns and thinks.
    - Despite significant differences between artificial neural networks and biological brains, the initial biological inspiration remains relevant.
- **Historical Development**:
    
    - Neural networks were first developed in the 1950s.
    - They fell out of favor but gained popularity again in the 1980s and early 1990s, particularly in applications like handwritten digit recognition.
    - Interest waned again in the late 1990s, but there was a resurgence around 2005 with the advent of deep learning.
- **Deep Learning Emergence**:
    
    - Deep learning, closely related to neural networks, gained popularity due to its appealing name and the significant improvements it brought to various applications.
    - Deep learning initially made a major impact on speech recognition, followed by computer vision, and later on natural language processing and other fields.
- **Modern Applications**:
    
    - Neural networks are now used in a wide range of applications, including climate change, medical imaging, online advertising, and product recommendations.
- **Biological Analogy**:
    
    - The human brain consists of neurons that send electrical impulses to each other, forming the basis of thought.
    - Artificial neural networks use simplified mathematical models to mimic this process, although they do not closely resemble the actual workings of the brain.
- **Components of Neurons**:
    
    - Biological neurons have dendrites (inputs) and axons (outputs).
    - Artificial neurons perform computations on input numbers and produce output numbers, which can then be inputs to other neurons.
- **Shift from Biological to Engineering Motivation**:
    
    - Research in deep learning has shifted from a biological motivation to an engineering focus, seeking to build more effective algorithms.
    - There are still many unknowns about how the human brain works, and future discoveries in neuroscience are expected.
- **Data and Performance**:
    
    - The rise of digital data has enabled the training of larger neural networks.
    - Traditional algorithms like logistic regression struggled to improve with more data, but neural networks could scale and perform better with increasing data.
- **Hardware Advancements**:
    
    - The rise of GPUs has significantly contributed to the growth of deep learning by providing the necessary computational power.
- **Resurgence and Success**:
    
    - Neural networks' resurgence in the 2000s was driven by the availability of large datasets and powerful computational resources.
    - They have since revolutionized multiple fields by achieving unprecedented performance in various applications.
#### Single Neuron Example

1. **Input Feature**: Price of the T-shirt.
2. **Logistic Regression**: Uses the sigmoid function to predict the probability of the T-shirt being a top seller.
3. **Output**: Probability value, denoted as $a$(activation).

#### Building a Simple Neural Network

1. **Multiple Features**: Price, shipping costs, marketing amount, material quality.
2. **Neurons in Hidden Layer**:
    - **Affordability**: Depends on price and shipping costs.
    - **Awareness**: Depends on marketing amount.
    - **Perceived Quality**: Depends on price and material quality.
3. **Output Layer**: Takes inputs from the hidden layer (affordability, awareness, perceived quality) to predict the probability of being a top seller.

#### Neural Network Layers

1. **Input Layer**: Vector of features (e.g., [price, shipping costs, marketing, materia l quality]).
2. **Hidden Layer**: Computes intermediate activations (e.g., affordability, awareness, perceived quality).
3. **Output Layer**: Final prediction (e.g., probability of being a top seller).

#### Simplified Neural Network

- Each neuron in a layer has access to all features from the previous layer.
- Layers are connected such that outputs from one layer serve as inputs to the next.
- Neural networks can learn to optimize feature combinations automatically.

#### Example Neural Network Architectures

1. **Single Hidden Layer**:
    - Input features → Hidden layer (3 neurons) → Output layer (1 neuron).
2. **Multiple Hidden Layers**:
    - Input features → Hidden layer 1 → Hidden layer 2 → Output layer.
    - More layers can lead to better feature extraction and improved predictions.

#### Key Concepts

- **Activation (a)**: The output of a neuron.
- **Hidden Layer**: Intermediate layer between input and output, used for feature learning.
- **Architecture**: Number of layers and neurons per layer, affecting model performance.