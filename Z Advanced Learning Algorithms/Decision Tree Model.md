# Advanced Learning Algorithms: Decision Trees and Tree Ensembles

## Overview
- Decision trees are powerful and widely used in many applications.
- Despite their success, they often receive less attention in academia.
- This week, we will explore decision trees and learn how to use them effectively.

## Example: Cat Classification
- You are running a cat adoption center and want to classify animals as cats or not.
- Dataset: 10 examples with features (ear shape, face shape, whiskers) and labels (cat or not).
- Features are categorical with binary values (e.g., pointy or floppy ears).

## What is a Decision Tree?
- A decision tree model looks like a tree with nodes and branches.
- **Nodes**: Represent decisions based on feature values.
  - **Root Node**: The topmost node.
  - **Decision Nodes**: Internal nodes that split based on feature values.
  - **Leaf Nodes**: Terminal nodes that make a prediction.

## Example Decision Tree
- A new test example (cat with pointy ears, round face, whiskers present):
  - Start at the root node (ear shape).
  - Follow the left branch for pointy ears.
  - Next, check the face shape.
  - Follow the branch for round face.
  - Reach the leaf node predicting "cat".

## Decision Tree Terminology
- **Root Node**: The topmost node where the tree starts.
- **Decision Nodes**: Nodes that split based on feature values.
- **Leaf Nodes**: Nodes that make predictions.

## Building Decision Trees
- Various decision trees can be constructed for the same application.
- The goal is to choose a tree that performs well on training, validation, and test sets.
- The learning algorithm selects the best tree from many possible trees.

## Example Decision Trees
- Example 1: Split on ear shape, then whiskers.
- Example 2: Split on ear shape, then face shape.
- Example 3 and 4: Different combinations of feature splits.

# Building a Decision Tree

## Overview
- The process of building a decision tree involves several key steps and decisions.

## Step-by-Step Process

1. **Decide Feature for Root Node**
   - Choose a feature to split the data at the root node.
   - Example: Split on the "ear shape" feature.
   - Split the dataset into subsets based on the chosen feature value.

2. **Split Data Based on Feature**
   - For each subset, choose the next feature to split.
   - Example: Split the left subset based on "face shape".

3. **Create Leaf Nodes**
   - If a subset is pure (all cats or all dogs), create a leaf node with the prediction.
   - Example: All cats -> create a "cat" prediction leaf node.

4. **Repeat for Remaining Subsets**
   - Repeat the process for the remaining subsets.
   - Example: Split the right subset based on "whiskers".

## Key Decisions

1. **Choosing Features to Split On**
   - Decide which feature to use at each node.
   - Aim to maximize purity of subsets (e.g., all cats or all dogs).
   - Use metrics like entropy to measure impurity and guide splits.

2. **When to Stop Splitting**
   - Stop splitting when subsets are pure (all cats or all dogs).
   - Set a maximum tree depth to prevent the tree from getting too large.
   - Stop if further splits result in minimal improvement in purity.
   - Stop if the number of examples in a subset is below a threshold.

## Measuring Purity
- Use metrics like entropy to estimate impurity and decide on splits.
- Aim to reduce impurity at each split.

## Practical Tips
- The decision tree algorithm can feel complex due to its many components.
- Various researchers have contributed refinements over time.
- Key ideas and practical suggestions will be covered to make the algorithm effective.
- Using open source packages can simplify implementation and decision-making.

[[Entropy when measuring purity]]


[[Random Forest Algorithm]]
[[XGBoost Algorithm]]

# Choosing Between Decision Trees and Neural Networks

## Decision Trees and Tree Ensembles

### When to Use
- **Tabular Data (Structured Data)**:
  - Suitable for datasets that look like spreadsheets.
  - Examples include housing price prediction with features like house size, number of bedrooms, etc.
  - Works for both classification and regression tasks.

### Advantages
- **Fast Training**:
  - Quick to train, allowing for faster iteration in the machine learning development loop.
- **Interpretability**:
  - Small decision trees are human interpretable.
  - Note: Interpretability diminishes with larger ensembles of trees.
- **Efficiency**:
  - Training can be computationally inexpensive, especially for small trees.

### Recommendations
- **XGBoost**:
  - Preferred for most applications due to its performance and efficiency.
  - Tree ensembles (like XGBoost) are more powerful than single decision trees.
  - Only use a single decision tree if computational resources are extremely limited.

### Limitations
- **Unstructured Data**:
  - Not recommended for images, video, audio, or text.

## Neural Networks

### When to Use
- **All Types of Data**:
  - Effective on both structured (tabular) and unstructured data (images, video, audio, text).
  - Suitable for mixed data containing both structured and unstructured components.

### Advantages
- **Flexibility**:
  - Works well across diverse data types.
- **Transfer Learning**:
  - Enables pre-training on large datasets, which is crucial for good performance with smaller datasets.
- **Integration**:
  - Easier to integrate multiple neural networks in a system compared to decision trees.

### Limitations
- **Training Time**:
  - Large neural networks can be slow to train, impacting the speed of iterative development.

## Summary

### Decision Trees (including Tree Ensembles)
- **Pros**:
  - Fast training.
  - Effective on tabular data.
  - Human interpretability (for small trees).
  - Computationally efficient.
- **Cons**:
  - Not suitable for unstructured data.
  - Large ensembles can become complex and less interpretable.

### Neural Networks
- **Pros**:
  - Versatile across various data types.
  - Beneficial transfer learning capabilities.
  - Easier integration of multiple models.
- **Cons**:
  - Slower training times, especially for large networks.

## Conclusion
- Use **decision trees** or **tree ensembles** (e.g., XGBoost) for structured data and when fast training is needed.
- Use **neural networks** for unstructured data or when leveraging transfer learning is advantageous.
- Both algorithms are powerful; the choice depends on the specific dataset and application requirements.

## Final Note
- Congratulations on completing the course on Advanced Learning Algorithms!
- Look forward to the next course on unsupervised learning.
- Practice with the provided quizzes and labs to reinforce your understanding.
- May the forest be with you!
