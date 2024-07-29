# Building a Decision Tree Ensemble: Random Forest

## Introduction to Random Forest

- **Tree Ensemble Algorithm**: Combines multiple decision trees to improve performance.
- **Random Forest**: A powerful tree ensemble algorithm better than a single decision tree.

## Generating an Ensemble of Trees

1. **Sampling with Replacement**:
   - Given a training set of size $M$.
   - For $B = 1$ to $B$, do the following:
     - Sample with replacement to create a new training set of size $M$.
     - Train a decision tree on this new training set.
   
2. **Example**:
   - Original training set: 10 examples.
   - Generate new training sets by sampling with replacement (some examples may repeat).
   - Train decision trees on these new sets.
   - Repeat this process $B$ times (typical $B \approx 100$).

3. **Making Predictions**:
   - Use the ensemble of trees to vote on the final prediction.
   - Larger $B$ generally improves performance but with diminishing returns.

## Bagged Decision Trees

- **Bagging**: The process of creating multiple training sets by sampling with replacement.
- **Bagged Decision Tree**: The ensemble of trees created through bagging.

## Random Forest Algorithm

1. **Issue with Bagged Trees**:
   - Sometimes, different trees use the same splits at the root node, reducing diversity.

2. **Randomization to Improve Diversity**:
   - At each node, instead of choosing the best feature from all $N$ features, choose from a random subset of $K$ features.
   - Typically, $K = \sqrt{N}$.
   - This ensures more diverse trees and thus more robust predictions.

3. **Steps of the Random Forest Algorithm**:
   - For each tree:
     - Sample with replacement to create a new training set.
     - For each node in the tree, select $K$ random features.
     - Choose the best feature to split from these $K$ features.

## Example Calculation

- **Original Data**:
  - Features: Ear Shape, Face Shape, Whiskers.

- **Random Subset**:
  - Suppose $N = 3$ (three features), then $K = \sqrt{3} \approx 1.73 \approx 2$.
  - Select 2 random features from the 3 available.

- **Weighted Average Entropy**:
  - Let $H(root)$ be the entropy of the root node.
  - For each split, calculate the weighted average entropy of the left and right subsets.
  - Information Gain: $IG = H(root) - (w_{left} \cdot H(left) + w_{right} \cdot H(right))$.
  - Choose the split that maximizes information gain.

## Robustness of Random Forest

- **Averaging Over Changes**:
  - The sampling with replacement procedure explores small changes to the data.
  - Averaging over these changes makes the algorithm robust to small variations in the training set.

## Conclusion

- **Random Forest**: Effective and robust algorithm for classification and regression tasks.
- **Next Topic**: Boosted Decision Trees (e.g., XGBoost) which often perform even better.

## Fun Fact

- **Joke**: Where does a machine learning engineer go camping? In a random forest!

I hope this provides a clear understanding of the Random Forest algorithm and how to implement it effectively in your work. Stay tuned for the next video on Boosted Decision Trees!
