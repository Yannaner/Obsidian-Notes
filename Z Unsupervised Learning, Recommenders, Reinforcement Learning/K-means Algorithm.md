# K-Means Clustering Algorithm

Guarentee to converge, always gonna reduce the Cost function, fi it goes up then theres a bug in the code.

## Definition
K-Means is a type of unsupervised learning algorithm used to partition a dataset into $K$ clusters, where each data point belongs to the cluster with the nearest mean (centroid).

## Key Concepts
- **Cluster (C)**: A group of data points that are similar to each other.
- **Centroid ($\mu$)**: The mean position of all the points in a cluster.
- **Assignment ($C_i$)**: The index of the cluster to which the training example $X_i$ is assigned.

## Cost Function
The K-means algorithm minimizes a specific cost function, also known as the **distortion function**. This cost function measures the average squared distance between each data point and the centroid of the cluster to which it is assigned.

### Notation
- $C_i$: Index of the cluster to which training example $X_i$ is currently assigned.
- $\mu_k$: Location of cluster centroid $k$.
- $\mu_{C_i}$: Cluster centroid of the cluster to which example $X_i$ is assigned.

### Cost Function Formula(Also called Distortion)
The cost function $J$ is defined as:
$$J(C_1, \ldots, C_m, \mu_1, \ldots, \mu_K) = \frac{1}{m} \sum_{i=1}^{m} \|X_i - \mu_{C_i}\|^2$$
Where:
- $m$ is the number of training examples.
- $\|X_i - \mu_{C_i}\|^2$ is the squared distance between training example $X_i$ and the centroid of the cluster it is assigned to.

## K-Means Algorithm Steps
### Step 1: Initialize Centroids
Randomly select $K$ data points as initial centroids.

### Step 2: Assign Points to Closest Centroid
Assign each data point to the cluster with the nearest centroid. This step minimizes the cost function $J$ by finding the closest centroid for each data point.

### Step 3: Update Centroids
Recompute the centroids by calculating the mean of all data points assigned to each cluster. This step minimizes the cost function $J$ by finding the optimal position for each centroid.

### Step 4: Repeat
Repeat steps 2 and 3 until the assignments no longer change or the cost function $J$ stops decreasing.

## Optimization and Convergence
- The K-means algorithm iteratively optimizes the cost function $J$ and is guaranteed to converge, meaning the cost function will either decrease or remain the same in each iteration.
- Convergence is typically detected when the cost function $J$ no longer changes significantly or remains constant over iterations.

## Example
Consider a simplified example with two cluster centroids and a single training example:
- If the example $X_i$ is closer to centroid 2 than centroid 1, assign $X_i$ to centroid 2 to minimize the squared distance.

## Cost Function Interpretation
The cost function measures the "distortion" or how well the data points are clustered around their centroids. Minimizing this function ensures that the clusters are as tight as possible.

## Practical Tips
- **Random Initialization**: Use multiple random initializations of the cluster centroids to find better clusters and avoid local minima.
- **Convergence Criteria**: Stop the algorithm when the cost function $J$ stops decreasing or changes very slowly.
- **Compute Cost Function**: Monitor the cost function to ensure it is decreasing and to determine if the algorithm has converged.

## References
- "Pattern Recognition and Machine Learning" by Christopher Bishop
- "Introduction to Data Mining" by Pang-Ning Tan, Michael Steinbach, and Vipin Kumar
- Scikit-learn documentation on clustering algorithms: https://scikit-learn.org/stable/modules/clustering.html


# K-Means Initialization
One good method is to run multiple times 

## Initialization of Cluster Centroids

The first step of the K-means clustering algorithm is to choose random locations as the initial guesses for the cluster centroids $\mu_1$ through $\mu_K$. But how do you actually take that random guess? Let's take a look at that, as well as how you can take multiple attempts at the initial guesses with $\mu_1$ through $\mu_K$ that will result in finding a better set of clusters.

### Step 1: Initial Guess
When running K-means, you should pretty much always choose the number of cluster centroids $K$ to be less than the number of training examples $m$. It doesn't really make sense to have $K > m$ because there won't be enough training examples to have at least one per cluster centroid. For example, if $K = 2$ and $m = 30$.

To choose the cluster centroids, the most common way is to randomly pick $K$ training examples. For instance, if I were to randomly pick two training examples, I might end up picking this one and this one, and then set $\mu_1$ through $\mu_K$ equal to these $K$ training examples.

### Random Initialization
If this was your random initialization and you were to run K-means, you might end up with K-means deciding that these are the two clusters in the dataset. Note that this method of initializing the cluster centroids is slightly different from initializing the centroids to be just random points rather than sitting on top of specific training examples.

With this method, there is a chance that you end up with an initialization where, for example, the red cross is here and the blue cross is there. Depending on how you choose the random initial centroids, K-means will end up picking a different set of clusters for your dataset.

### Example with Three Clusters
Consider a more complex example where we try to find three clusters ($K = 3$):

1. **First Initialization**: If you were to run K-means with one random initialization of the cluster centroids, you might get this result, which looks like a pretty good clustering of the data into three clusters.
2. **Second Initialization**: With a different initialization, say you happen to initialize two of the cluster centroids within one group of points and one within another group, after running K-means, you might end up with a clustering that doesn't look as good. This could be a local optimum.

### Local Optima
The K-means algorithm might get stuck in a local minimum, depending on the initialization. To give K-means multiple shots at finding the best local optimum, you can run it multiple times and then select the best result.

### Multiple Runs
To increase the chances of finding the best clustering:
1. **Run K-means multiple times** with different random initializations.
2. **Compute the cost function $J$** for all the solutions.
3. **Select the clustering with the lowest cost function $J$**.

### Formal Algorithm
If you want to use 100 random initializations for K-means:
1. Run K-means 100 times, each time with a different random initialization of the centroids using the method described.
2. For each run, compute the cost function $J$ after the algorithm converges.
3. Finally, select the set of clusters with the lowest cost function $J$.

Using multiple random initializations will often give you a much better set of clusters with a lower distortion function than running K-means only once. Running this procedure 50 to 1000 times is common, as it balances computational expense with the likelihood of finding a good clustering.

When using the K-means algorithm, always use more than one random initialization to minimize the distortion cost function and find a better choice for the cluster centroids.

# Deciding the Number of Clusters for K-Means

## Key Concepts
- **K-means Algorithm**: Requires an input $K$, which is the number of clusters to be found.
- **Ambiguity in Choosing $K$**: The right number of clusters can be subjective and context-dependent.

## Methods for Choosing $K$
1. **Elbow Method**:
   - Run K-means with various values of $K$.
   - Plot the cost function $J$ against the number of clusters.
   - Identify the "elbow" point where the cost function decreases more slowly, suggesting a suitable $K$.
   - The elbow represents a trade-off between the number of clusters and the reduction in cost function.

2. **Evaluating Downstream Purposes**:
   - Often, clusters are used for a specific application or downstream purpose.
   - Choose $K$ based on how well the clusters perform for that purpose.
   - Example: For t-shirt sizing, compare clusters for $K = 3$ (small, medium, large) vs. $K = 5$ (extra small, small, medium, large, extra large).
     - Evaluate the trade-off between better fit (more clusters) and cost (fewer clusters).

3. **Avoid Minimizing Cost Function $J$ Directly**:
   - Minimizing $J$ by choosing the largest possible $K$ is not effective.
   - More clusters will always reduce $J$, but may not be practical or meaningful.

## Practical Example
- **T-shirt Sizing**:
  - Run K-means for $K = 3$ and $K = 5$.
  - Evaluate clusters based on fit quality vs. manufacturing and shipping costs.

- **Image Compression**:
  - Trade-off between image quality and compression size.
  - Decide $K$ based on desired balance between visual quality and file size.

## Conclusion
- Choosing $K$ is often application-specific and involves trade-offs.
- Use methods like the elbow method for initial insights.
- Ultimately, evaluate $K$ based on how well it serves the specific application or downstream purpose.

```python
def find_closest_centroids(X, centroids):
    """
    Computes the centroid memberships for every example
    
    Args:
        X (ndarray): (m, n) Input values      
        centroids (ndarray): (K, n) centroids
    
    Returns:
        idx (array_like): (m,) closest centroids
    
    """

    # Set K
    K = centroids.shape[0]

    # You need to return the following variables correctly
    idx = np.zeros(X.shape[0], dtype=int)

    ### START CODE HERE ###
    for i in range(X.shape[0]):
        # Array to hold distance between X[i] and each centroids[j]
        distance = [] 
        for j in range(centroids.shape[0]):
            norm_ij = np.linalg.norm(X[i] - centroids[j])
            distance.append(norm_ij)

        idx[i] = np.argmin(distance)
     ### END CODE HERE ###
    
    return idx
```

```python
def compute_centroids(X, idx, K):
    """
    Returns the new centroids by computing the means of the 
    data points assigned to each centroid.
    
    Args:
        X (ndarray):   (m, n) Data points
        idx (ndarray): (m,) Array containing index of closest centroid for each 
                       example in X. Concretely, idx[i] contains the index of 
                       the centroid closest to example i
        K (int):       number of centroids
    
    Returns:
        centroids (ndarray): (K, n) New centroids computed
    """
    
    # Useful variables
    m, n = X.shape
    
    # You need to return the following variables correctly
    centroids = np.zeros((K, n))
    
    ### START CODE HERE ###
    for k in range(K):
        points = X[idx == k] 
        centroids[k]=np.mean(points,axis=0)
        
        
    ### END CODE HERE ## 
    
    return centroids
```

