# Efficient Fine-Tuning Methods: LoRA and Prompt Tuning

## Overview

This lesson explores efficient methods for fine-tuning large language models (LLMs) without the need for extensive retraining of all parameters.

## LoRA (Low-Rank Adaptation)
- **Objective**: Efficiently update model weights without retraining all parameters.
- **Method**: Uses rank decomposition matrices to update parameters efficiently.
- **Benefits**: Comparable performance to full fine-tuning with reduced computational cost.

## Prompt Tuning
- **Concept**: Adds additional trainable tokens (soft prompts) to the input prompt, optimizing through supervised learning.
- **Difference from Prompt Engineering**:
  - **Prompt Engineering**: Manually crafting prompts to get desired outputs.
  - **Prompt Tuning**: Trainable tokens are added and optimized by the model.
- **Mechanism**:
  - Soft prompts are virtual tokens within the continuous multidimensional embedding space.
  - During training, the LLM's weights are frozen; only the soft prompts are updated.
- **Performance**:
  - Performs comparably to full fine-tuning in large models (e.g., 10 billion parameters).
  - More efficient and flexible than full fine-tuning, with small disk space requirements.

## Performance Comparison
- **Full Fine-Tuning**: Highest performance, especially for smaller models.
- **Prompt Tuning**: Approaches full fine-tuning performance as model size increases.
- **Prompt Engineering**: Lower performance compared to prompt tuning and fine-tuning.

## Key Insights
- **Soft Prompts**: Trainable tokens can take on any value within the embedding space, forming tight semantic clusters related to the task.
- **LoRA and Prompt Tuning**: Both methods offer efficient fine-tuning, reducing the computational resources required.

## Practical Applications
- **LoRA**: Broadly used for various tasks and datasets, offering a good balance between performance and computational efficiency.
- **Prompt Tuning**: Flexible and lightweight, suitable for quickly adapting models to new tasks.

## Recap
- **Instruction Fine-Tuning**: Adapting foundation models with specific prompts and datasets, effective across diverse NLP tasks.
- **PEFT (Parameter Efficient Fine-Tuning)**: Includes methods like LoRA and Prompt Tuning to reduce compute requirements.
- **QLoRA**: Combines LoRA with quantization techniques to further reduce memory usage.
