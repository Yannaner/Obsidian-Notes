![[Pasted image 20240805111708.png]]# Transformer Architecture

The Transformer architecture is a neural network model introduced in the paper "Attention is All You Need" by Vaswani et al. in 2017. It has become the foundation of many large language models (LLMs) such as GPT-3, BERT, and T5.

## Key Components

### 1. Self-Attention Mechanism
- Allows the model to weigh the importance of different words in a sequence when encoding or decoding.
- Each word in a sequence can attend to every other word, capturing relationships regardless of their distance in the text.

	[[Tokenizer]]
Encode only, Encoder decoder models, decoder only model



### 2. Multi-Head Attention
- Consists of several attention layers running in parallel, enabling the model to focus on different parts of the sequence simultaneously.
- Helps capture various aspects of word relationships, enhancing the model's understanding of context.

### 3. Positional Encoding
- Since Transformers don't inherently understand word order, positional encoding adds information about the position of each word in the sequence.
- This helps the model recognize the order and structure of the input.

### 4. Feed-Forward Networks
- After the attention layers, the model uses fully connected feed-forward neural networks to process the attention outputs.
- These layers help refine the representation of the input for the next stages.

### 5. Layer Normalization and Residual Connections
- **Layer Normalization**: Stabilizes and accelerates training by normalizing inputs across each layer.
- **Residual Connections**: Adds the input of each layer to its output, helping preserve information and improving gradient flow during training.

### 6. Encoder-Decoder Structure (Optional)
- In some models, the Transformer is split into an encoder (processes input) and a decoder (generates output).
- This structure is particularly useful for tasks like machine translation.

## Usage and Tasks for Large LLMs and Generative AI

### 1. Text Generation
- **Creative Writing**: Storytelling, poetry, or content creation.
- **Text Completion**: Autocompleting sentences or paragraphs.

### 2. Natural Language Understanding (NLU)
- **Sentiment Analysis**: Determining the sentiment behind a piece of text.
- **Named Entity Recognition (NER)**: Identifying entities like names, dates, and locations in text.

### 3. Translation and Summarization
- **Machine Translation**: Translating text from one language to another.
- **Summarization**: Condensing long documents into concise summaries.

### 4. Conversational Agents
- **Chatbots**: Interacting with users in natural language for customer service, personal assistance, or entertainment.
- **Virtual Assistants**: Performing tasks like setting reminders, answering queries, or managing schedules.

### 5. Code Generation and Debugging
- **Code Assistance**: Generating code snippets based on natural language descriptions.
- **Code Debugging**: Identifying and fixing errors in code through natural language interaction.

### 6. Image and Audio Generation (Multimodal AI)
- **Image Generation**: Creating images from textual descriptions (e.g., DALL-E).
- **Audio Generation**: Generating music, sound effects, or speech from text.

### 7. Data Augmentation
- **Training Data Creation**: Generating synthetic data to augment training datasets for machine learning models.

### 8. Personalization and Recommendations
- **Personalized Content**: Tailoring content like news articles or recommendations based on user preferences and behavior.
![[Pasted image 20240805112947.png]]

Top-k: Select and output from top-k result after applying random-weighted strategy using probabilities
Top-p: Select an output using random-weighted strategy with top ranked consecutive results by  probability and with a cumulative probability <=p

Temperature: The higher the temperature the higher the randomness(more creative)
![[Pasted image 20240805121104.png]]

Generative AI poject life cycle:
![[Pasted image 20240805121554.png]]


