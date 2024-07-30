# Mean Normalization in Collaborative Filtering

In linear regression, feature normalization helps the algorithm run faster. Similarly, in building a recommender system with numeric ratings (like movie ratings from 1 to 5 or 0 to 5 stars), mean normalization can make the algorithm run more efficiently and perform better. Let's explore how mean normalization works and why it's beneficial.

## Dataset and Cost Function

Here's the dataset we've been using, with ratings from multiple users for different movies. Let's introduce a new user, Eve, who hasn't rated any movies yet. Our cost function to learn the parameters for the model is as follows:
$$ J(w, b, x) = \sum_{i=1}^{m} \sum_{j:r(i,j)=1} \left( w^{(j)} \cdot x^i + b^{(j)} - y(i,j) \right)^2 + \frac{\lambda}{2} \left( \sum_{j=1}^{\nu} \sum_{k=1}^{n} \left( w_k^{(j)} \right)^2 + \sum_{i=1}^{m} \sum_{k=1}^{n} \left( x_k^i \right)^2 \right) $$

If we train a collaborative filtering algorithm on this dataset, the parameters $w$ for Eve might end up being $\mathbf{0}$ and $b^{(5)} = 0$. This leads to predicting a rating of 0 stars for all movies for Eve, which is not useful.

## Mean Normalization

Mean normalization helps to make better predictions for users like Eve who haven't rated any movies. Here's how it works:

1. **Organize Ratings**: Convert the dataset into a matrix form where rows represent users and columns represent movies.

2. **Compute Average Ratings**: For each movie, compute the average rating given by users.
   - Movie 1: $(5 + 5 + 0 + 0)/4 = 2.5$
   - Movie 2: $(5 + 0)/2 = 2.5$
   - Movie 3: $(4 + 0)/2 = 2.0$
   - Movie 4: $(4 + 0 + 0 + 5)/4 = 2.25$
   - Movie 5: $(0 + 5)/2 = 1.25$

   Collect these averages into a vector $\mu$.

3. **Normalize Ratings**: Subtract the mean rating for each movie from the individual ratings.
   - For Movie 1, User 1's rating becomes $5 - 2.5 = 2.5$.
   - For Movie 4, User 1's rating becomes $0 - 2.25 = -2.25$.

   Apply this to all ratings, including Eve's missing ratings, which are set to zero initially.

4. **Update Cost Function**: Replace the original ratings with the normalized ratings in the cost function.

## Making Predictions

When predicting ratings for a new user like Eve, after learning $w^{(j)}$, $b^{(j)}$, and $x^i$:
$$ \hat{y}^{(j)}(i) = w^{(j)} \cdot x^i + b^{(j)} $$
To get the original scale ratings, add back the mean rating:
$$ \hat{y}^{(j)}(i) = w^{(j)} \cdot x^i + b^{(j)} + \mu_i $$

For Eve, with $w^{(5)} = \mathbf{0}$ and $b^{(5)} = 0$, the predicted rating for Movie 1 is:
$$ \hat{y}^{(5)}(1) = 0 + 0 + 2.5 = 2.5 $$

This seems more reasonable than predicting zero stars.

## Benefits of Mean Normalization

1. **Better Initial Predictions**: For new users who haven't rated any movies, mean normalization provides a reasonable starting point by assuming they might rate movies similarly to the average rating.
2. **Faster Optimization**: Normalizing the mean of movie ratings to zero makes the optimization algorithm run faster.
3. **Improved Predictions**: It helps the algorithm make more reasonable predictions for users who have rated very few movies.

## Implementation in Practice

When implementing your recommender system, normalizing the rows (user ratings) should suffice. Normalizing columns (movie ratings) might be beneficial for new movies with no ratings, but normalizing rows is generally more crucial for handling new users.

![[Pasted image 20240725204509.png]]
