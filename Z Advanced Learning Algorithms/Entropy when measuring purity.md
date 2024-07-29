# Measuring Purity with Entropy


For information gain, the higher the number, the better the chose be
For purity number, the closer to 0.5 the better.
## Introduction
- **Entropy**: A measure of impurity or disorder in a set of data.
- High entropy = high impurity (mix of classes).
- Low entropy = low impurity (pure set of one class).

## Definition of Entropy

- **Entropy Function (H)**:
  $$H(p_1) = -p_1 \log_2 (p_1) - p_0 \log_2 (p_0)$$
  where:
  - $p_1$ = fraction of examples that are positive (e.g., cats).
  - $p_0$ = fraction of examples that are negative (e.g., not cats, dogs) = $1 - p_1$.

## Example Calculations

1. **Mixed Set** (3 cats, 3 dogs):
   - $p_1 = \frac{3}{6} = 0.5$
   - Entropy, $H(0.5) = 1$

2. **Mostly Cats** (5 cats, 1 dog):
   - $p_1 = \frac{5}{6} \approx 0.83$
   - Entropy, $H(0.83) \approx 0.65$

3. **All Cats** (6 cats):
   - $p_1 = \frac{6}{6} = 1$
   - Entropy, $H(1) = 0$

4. **Mostly Dogs** (2 cats, 4 dogs):
   - $p_1 = \frac{2}{6} \approx 0.33$
   - Entropy, $H(0.33) \approx 0.92$

5. **All Dogs** (0 cats, 6 dogs):
   - $p_1 = 0$
   - Entropy, $H(0) = 0$

## Entropy Function Characteristics

- **Curve**:
  - Highest at $p_1 = 0.5$ (most impure).
  - Lowest at $p_1 = 0$ or $p_1 = 1$ (pure sets).

## Handling Edge Cases

- **Zero Fraction**: $0 \log_2 (0)$
  - Convention: $0 \log_2 (0) = 0$

## Comparison with Other Criteria

- **Gini Index**: Another impurity measure similar to entropy.
  - Often used in decision trees.
  - Focus on entropy for simplicity.

## Next Steps

- Use entropy to decide which feature to split on in decision trees.

## Information Gain

- **Information Gain**: The reduction in entropy when a dataset is split on a feature.
- **Formula**: 
  $IG(T, A) = H(T) - \sum_{v \in Values(A)} \frac{|T_v|}{|T|} \times H(T_v)$
  where:
  - $T$ = the original dataset.
  - $A$ = the feature on which to split.
  - $T_v$ = the subset of $T$ where feature $A$ has value $v$.
  - $H(T)$ = entropy of the original dataset.
  - $H(T_v)$ = entropy of the subset $T_v$.

## Example

Let's use the example of deciding what feature to use at the root node of the decision tree we were building just now for recognizing cats versus not cats.

### Ear Shape
- Left subset: 5 examples, 4 cats ($p_1 = \frac{4}{5} = 0.8$)
- Right subset: 5 examples, 1 cat ($p_1 = \frac{1}{5} = 0.2$)
- Entropy:
  - $H(0.8) \approx 0.72$
  - $H(0.2) \approx 0.72$
- Weighted average entropy:
  - $\frac{5}{10} \times 0.72 + \frac{5}{10} \times 0.72 = 0.72$
- Information gain:
  - $H(root) - 0.72 = 1 - 0.72 = 0.28$

### Face Shape
- Left subset: 7 examples, 4 cats ($p_1 = \frac{4}{7} \approx 0.57$)
- Right subset: 3 examples, 1 cat ($p_1 = \frac{1}{3} \approx 0.33$)
- Entropy:
  - $H(0.57) \approx 0.99$
  - $H(0.33) \approx 0.92$
- Weighted average entropy:
  - $\frac{7}{10} \times 0.99 + \frac{3}{10} \times 0.92 \approx 0.97$
- Information gain:
  - $H(root) - 0.97 = 1 - 0.97 = 0.03$

### Whiskers
- Left subset: 4 examples, 3 cats ($p_1 = \frac{3}{4} = 0.75$)
- Right subset: 6 examples, 2 cats ($p_1 = \frac{2}{6} \approx 0.33$)
- Entropy:
  - $H(0.75) \approx 0.81$
  - $H(0.33) \approx 0.92$
- Weighted average entropy:
  - $\frac{4}{10} \times 0.81 + \frac{6}{10} \times 0.92 \approx 0.87$
- Information gain:
  - $H(root) - 0.87 = 1 - 0.87 = 0.13$

### Choosing the Best Split
- Compare information gain values:
  - Ear Shape: 0.28
  - Face Shape: 0.03
  - Whiskers: 0.13
- Highest information gain: Ear Shape (0.28)

## Conclusion

- Information gain helps us choose the feature that best splits the data.
- Highest information gain = greatest reduction in impurity.
- Use this to build effective decision trees by choosing features that maximize information gain at each node.

## Additional Notation

- **Weights**:
  - $w_{left}$: fraction of examples in the left subset.
  - $w_{right}$: fraction of examples in the right subset.
- **Example**:
  - Ear Shape: $w_{left} = \frac{5}{10}$, $w_{right} = \frac{5}{10}$
  - Face Shape: $w_{left} = \frac{7}{10}$, $w_{right} = \frac{3}{10}$

## Formal Definition of Information Gain

- Let $p_1^{left}$ be the fraction of positive examples in the left subset.
- Let $w_{left}$ be the fraction of total examples that went to the left subset.
- Let $p_1^{right}$ be the fraction of positive examples in the right subset.
- Let $w_{right}$ be the fraction of total examples that went to the right subset.
- Let $p_1^{root}$ be the fraction of positive examples in the root node.
- Information gain is then:


  $$IG = H(p_1^{root}) - \left( w_{left} \cdot H(p_1^{left}) + w_{right} \cdot H(p_1^{right}) \right)$$

With this definition, you can calculate the information gain for any feature and choose the one that gives the highest gain to split on in the node of a decision tree.



How to create a decision tree
![[Pasted image 20240718203909.png]]


[[One Hot Encoding]]

```python
def entropy(p):
    if p == 0 or p == 1:
        return 0
    else:
        return -p * np.log2(p) - (1- p)*np.log2(1 - p)
    
print(entropy(0.5))
```
```python
def split_indices(X, index_feature):
    """Given a dataset and a index feature, return two lists for the two split nodes, the left node has the animals that have 
    that feature = 1 and the right node those that have the feature = 0 
    index feature = 0 => ear shape
    index feature = 1 => face shape
    index feature = 2 => whiskers
    """
    left_indices = []
    right_indices = []
    for i,x in enumerate(X):
        if x[index_feature] == 1:
            left_indices.append(i)
        else:
            right_indices.append(i)
    return left_indices, right_indices
```
```python
def weighted_entropy(X,y,left_indices,right_indices):
    """
    This function takes the splitted dataset, the indices we chose to split and returns the weighted entropy.
    """
    w_left = len(left_indices)/len(X)
    w_right = len(right_indices)/len(X)
    p_left = sum(y[left_indices])/len(left_indices)
    p_right = sum(y[right_indices])/len(right_indices)
    
    weighted_entropy = w_left * entropy(p_left) + w_right * entropy(p_right)
    return weighted_entropy
```
```python
def information_gain(X, y, left_indices, right_indices):
    """
    Here, X has the elements in the node and y is theirs respectives classes
    """
    p_node = sum(y)/len(y)
    h_node = entropy(p_node)
    w_entropy = weighted_entropy(X,y,left_indices,right_indices)
    return h_node - w_entropy
```



 for i in range(len(y)):
        if y[i] == 1:
            count=count+1
    p = count/len(y)
    entropy = -p * np.log2(p) - (1- p)*np.log2(1 - p)
        
        
        