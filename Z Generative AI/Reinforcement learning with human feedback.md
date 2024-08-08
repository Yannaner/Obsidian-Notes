Proximal Policy Optimization
# Proximal Policy Optimization (PPO) in Reinforcement Learning

## What is PPO?
PPO stands for **Proximal Policy Optimization**, a popular reinforcement learning (RL) algorithm. PPO is used to optimize a policy, such as an LLM, making it more aligned with human preferences by making small, stable updates to the model.

## How PPO Works
PPO operates in two main phases:
1. **Phase I**: The LLM generates responses to various prompts. The reward model then evaluates these responses based on how well they align with human preferences (e.g., helpfulness, harmlessness).
2. **Phase II**: The model's weights are updated based on the calculated rewards, aiming to improve alignment with human preferences while keeping changes within a small, stable region (trust region).

## Key Components of PPO
- **Reward Model**: Captures human preferences and provides feedback on the LLM's responses.
- **Value Function**: Estimates the expected total reward for a given state, helping evaluate the quality of completions.
- **Value Loss**: The difference between the actual future reward and the value function's estimate. Minimizing this loss helps make future reward estimates more accurate.

## Policy Objective
- The PPO policy objective seeks to maximize the expected reward by adjusting the LLM's weights. The objective involves:
  - **Probability Ratio**: The ratio of the new policy's probability of taking an action to the old policy's probability.
  - **Advantage Term**: Estimates how much better or worse the current action is compared to others.
  - **Trust Region**: Ensures updates are within a safe, small region to maintain stability.

## Additional Components
- **Entropy Loss**: Balances the policy loss by maintaining model creativity, preventing it from becoming too deterministic.

## PPO in Large Language Models (LLMs)
- In the context of LLMs, PPO is used for fine-tuning models through Reinforcement Learning from Human Feedback (RLHF).
- **Iteration Process**: Over multiple cycles, the LLM is fine-tuned to better align with human preferences, eventually producing a more aligned LLM.

## Alternatives to PPO
- Other RL techniques like Q-learning can be used, but PPO is popular due to its balance of complexity and performance.
- New techniques like Direct Preference Optimization are being developed, offering simpler alternatives to RLHF.

## Conclusion
PPO is a crucial method for fine-tuning LLMs to align with human preferences, combining stability with effective performance improvements.



Reward hacking


# KL divergence

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/sMBhUqOTS7a1y8Ho5vF9qQ_4ea0db1de2764787b09f681255045df1_image.png?expiry=1723248000000&hmac=6JxHAqiYX2m4pUthJ7YNM0H9EnOja5FPawiJP4iISvA)

KL-Divergence, or Kullback-Leibler Divergence, is a concept often encountered in the field of reinforcement learning, particularly when using the Proximal Policy Optimization (PPO) algorithm. It is a mathematical measure of the difference between two probability distributions, which helps us understand how one distribution differs from another. In the context of PPO, KL-Divergence plays a crucial role in guiding the optimization process to ensure that the updated policy does not deviate too much from the original policy.

In PPO, the goal is to find an improved policy for an agent by iteratively updating its parameters based on the rewards received from interacting with the environment. However, updating the policy too aggressively can lead to unstable learning or drastic policy changes. To address this, PPO introduces a constraint that limits the extent of policy updates. This constraint is enforced by using KL-Divergence.

To understand how KL-Divergence works, imagine we have two probability distributions: the distribution of the original LLM, and a new proposed distribution of an RL-updated LLM. KL-Divergence measures the average amount of information gained when we use the original policy to encode samples from the new proposed policy. By minimizing the KL-Divergence between the two distributions, PPO ensures that the updated policy stays close to the original policy, preventing drastic changes that may negatively impact the learning process.

A library that you can use to train transformer language models with reinforcement learning, using techniques such as PPO, is TRL (Transformer Reinforcement Learning). In [this link](https://huggingface.co/blog/trl-peft) you can read more about this library, and its integration with PEFT (Parameter-Efficient Fine-Tuning) methods, such as LoRA (Low-Rank Adaption). The image shows an overview of the PPO training setup in TRL.


*Constituitional AI*


