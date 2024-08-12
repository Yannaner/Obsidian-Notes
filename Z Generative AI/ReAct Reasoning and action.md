# ReAct: Reasoning and action
# Advanced Prompting Strategies for LLMs

## Overview of Structured Prompting with Python
- **PAL Framework**: PAL (Program-Aided Language) allows an LLM to write Python scripts to solve complex math problems. By linking the LLM to a Python interpreter, the application can run the code and return the answer.
- **Complex Workflows**: Most applications require the LLM to handle more complex workflows, including interactions with multiple external data sources.

## Introducing the ReAct Framework
- **What is ReAct?**: ReAct (Reasoning and Action) is a prompting strategy that combines chain-of-thought reasoning with action planning. Developed by researchers at Princeton and Google in 2022, ReAct was designed to tackle multi-step problems that require reasoning across multiple data sources.
- **Structured Prompts**:
  - **Thought**: The reasoning step that helps the LLM identify actions to take.
  - **Action**: Defined actions the LLM can take, such as searching for information.
  - **Observation**: New information provided by the action that feeds back into the reasoning process.

### Example: Determining Magazine Publication Dates
1. **Question**: Which of two magazines was created first?
2. **First Thought**: Identify that a search for both magazines is needed.
3. **First Action**: Search for the first magazine, "Arthur's Magazine."
4. **First Observation**: The model retrieves the start year of "Arthur's Magazine."
5. **Second Thought**: Identify the next step, searching for "First for Women."
6. **Second Action**: Search for the second magazine.
7. **Second Observation**: The start year of "First for Women" is retrieved.
8. **Third Thought**: Use the retrieved information to determine which magazine was published first.
9. **Final Action**: Finish the task and return the answer to the user.

### Key Components of ReAct
- **Allowed Actions**: The framework uses a limited set of actions (`search`, `lookup`, `finish`) defined in the prompt.
- **Instructions**: Prepend the instructions to the prompt, defining the task, specifying what "thought" and "action" mean, and listing allowed actions.
- **Inference Process**: Combine the ReAct example prompt with the instructions and the specific question to be answered, then pass the full prompt to the LLM for inference.

## Using LangChain for Application Development
- **What is LangChain?**: LangChain is a framework that provides modular components for working with LLMs, including prompt templates, memory for storing interactions, and tools for tasks like external data retrieval.
- **Chains and Agents**:
  - **Chains**: Predefined workflows connecting different components optimized for specific use cases.
  - **Agents**: Components that interpret user input and determine which actions or tools to use, providing flexibility in workflow execution.
- **Use of Agents**: LangChain includes agents for frameworks like PAL and ReAct, which can plan and execute actions based on user input.

## Considerations for Using LLMs
- **Model Size**: Larger models are generally more capable of understanding structured prompts and planning actions. Smaller models might require additional fine-tuning and may struggle with complex tasks.
- **Prototyping and Deployment**: Starting with a large model allows for faster prototyping and collecting user data, which can be used to fine-tune smaller models later.



[This paper](https://arxiv.org/abs/2210.03629) introduces ReAct, a novel approach that integrates verbal reasoning and interactive decision making in large language models (LLMs). While LLMs have excelled in language understanding and decision making, the combination of reasoning and acting has been neglected. ReAct enables LLMs to generate reasoning traces and task-specific actions, leveraging the synergy between them. The approach demonstrates superior performance over baselines in various tasks, overcoming issues like hallucination and error propagation. ReAct outperforms imitation and reinforcement learning methods in interactive decision making, even with minimal context examples. It not only enhances performance but also improves interpretability, trustworthiness, and diagnosability by allowing humans to distinguish between internal knowledge and external information.

In summary, ReAct bridges the gap between reasoning and acting in LLMs, yielding remarkable results across language reasoning and decision making tasks. By interleaving reasoning traces and actions, ReAct overcomes limitations and outperforms baselines, not only enhancing model performance but also providing interpretability and trustworthiness, empowering users to understand the model's decision-making process.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/1sTOKhNdQZ6PrrOKANlbRQ_f0c0bdfe18414de681e207ad6b23cef1_image.png?expiry=1723248000000&hmac=rlwsuPtJiZayAZKqrudh70jtocZpAF9BTiNNgzKSpW0)

**Image:** The figure provides a comprehensive visual comparison of different prompting methods in two distinct domains. The first part of the figure (1a) presents a comparison of four prompting methods: Standard, Chain-of-thought (CoT, Reason Only), Act-only, and ReAct (Reason+Act) for solving a HotpotQA question. Each method's approach is demonstrated through task-solving trajectories generated by the model (Act, Thought) and the environment (Obs). The second part of the figure (1b) focuses on a comparison between Act-only and ReAct prompting methods to solve an AlfWorld game. In both domains, in-context examples are omitted from the prompt, highlighting the generated trajectories as a result of the model's actions and thoughts and the observations made in the environment. This visual representation enables a clear understanding of the differences and advantages offered by the ReAct paradigm compared to other prompting methods in diverse task-solving scenarios.