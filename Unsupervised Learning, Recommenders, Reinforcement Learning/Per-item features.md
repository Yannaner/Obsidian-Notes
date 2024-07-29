![[Pasted image 20240725143030.png]]
![[Pasted image 20240725143152.png]]

# Developing a Recommender System with Movie Features

## Introduction

In this discussion, we'll explore how to develop a recommender system using features of each item, specifically movies. We will start with a dataset where four users have rated some but not all of five movies. Additionally, we will incorporate features of the movies, such as their romance and action content.

## Movie Features

Consider the following features for each movie:
- $X_1$: Romance content
- $X_2$: Action content

For example:
- **Love at Last**: $X_1 = 0.9$, $X_2 = 0.0$ (Highly romantic, not an action movie)
- **Nonstop Car Chases**: $X_1 = 0.1$, $X_2 = 1.0$ (Slightly romantic, high action)

We denote:
- $\nu$: Number of users (4)
- $m$: Number of movies (5)
- $n$: Number of features (2)

## Predicting Movie Ratings

To predict user ratings, we use a linear regression model:

$$ \hat{y}^{(j)}(i) = w^{(j)} \cdot X(i) + b^{(j)} $$

For example, for Alice (User 1):
- Suppose $w^{(1)} = [5, 0]$ and $b^{(1)} = 0$
- For **Cute Puppies of Love** with features $X(3) = [0.99, 0]$:

$$ \hat{y}^{(1)}(3) = 5 \cdot 0.99 + 0 \cdot 0 = 4.95 $$

This prediction aligns with Alice's high ratings for romantic movies.

## Cost Function

To learn the parameters $w^{(j)}$ and $b^{(j)}$, we minimize the following cost function for each user $j$:

$$ J(w^{(j)}, b^{(j)}) = \frac{1}{2m^{(j)}} \sum_{i:r(i,j)=1} \left( w^{(j)} \cdot X(i) + b^{(j)} - y(i,j) \right)^2 + \frac{\lambda}{2m^{(j)}} \sum_{k=1}^{n} \left( w_k^{(j)} \right)^2 $$

Where:
- $r(i,j) = 1$ if user $j$ has rated movie $i$, otherwise $r(i,j) = 0$
- $y(i,j)$ is the rating given by user $j$ to movie $i$
- $m^{(j)}$ is the number of movies rated by user $j$
- $\lambda$ is the regularization parameter

### Simplification
For convenience, we can remove the division by $m^{(j)}$:

$$ J(w^{(j)}, b^{(j)}) = \sum_{i:r(i,j)=1} \left( w^{(j)} \cdot X(i) + b^{(j)} - y(i,j) \right)^2 + \lambda \sum_{k=1}^{n} \left( w_k^{(j)} \right)^2 $$

## Learning Parameters for All Users

To learn the parameters for all users, sum the individual cost functions:

$$ J(\{w^{(j)}, b^{(j)}\}_{j=1}^{\nu}) = \sum_{j=1}^{\nu} \left( \sum_{i:r(i,j)=1} \left( w^{(j)} \cdot X(i) + b^{(j)} - y(i,j) \right)^2 + \lambda \sum_{k=1}^{n} \left( w_k^{(j)} \right)^2 \right) $$

## Optimization

Minimize this combined cost function using gradient descent or another optimization algorithm to find the best parameters $w^{(j)}$ and $b^{(j)}$ for all users.




# Collaborative filtering algorithm

# Collaborative Filtering: Learning Features from Data

In the previous discussion, we saw how to predict movie ratings using predefined features like $x_1$ (romance content) and $x_2$ (action content). But what if we don't have these features beforehand? In this discussion, we'll learn how to derive these features from the data itself.

## Dataset Overview

Consider a dataset where users rate different movies. Initially, we have some parameters $w$ and $b$ for each user but no predefined features for the movies.

For example, let's say we have learned the following parameters:
- User 1: $w^1 = [5, 0]$, $b^1 = 0$
- User 2: $w^2 = [5, 0]$, $b^2 = 0$
- User 3: $w^3 = [0, 5]$, $b^3 = 0$
- User 4: $w^4 = [0, 5]$, $b^4 = 0$

We predict user $j$'s rating on movie $i$ using:
$$ \hat{y}^{(j)}(i) = w^{(j)} \cdot x(i) + b^{(j)} $$
Given that all $b$ values are 0 for simplicity, the prediction simplifies to:
$$ \hat{y}^{(j)}(i) = w^{(j)} \cdot x(i) $$

## Guessing Features for Movies

Let's determine the features for a specific movie. Suppose Alice (User 1) rated Movie 1 with a score of 5. To make a good prediction, we need:
$$ w^1 \cdot x^1 \approx 5 $$
Given $w^1 = [5, 0]$, a possible feature vector for Movie 1 is $x^1 = [1, 0]$.

This satisfies:
$$ w^1 \cdot x^1 = 5 \cdot 1 + 0 \cdot 0 = 5 $$

Similarly, for Bob (User 2) who also rated Movie 1 with a score of 5, and other users' ratings, we can infer the feature vector $x^1$.

## Cost Function for Learning Features

To generalize, we define a cost function to learn the features $x^i$ for each movie $i$. The goal is to minimize the squared error between predicted and actual ratings:
$$ J(x^i) = \sum_{j:r(i,j)=1} \left( w^{(j)} \cdot x^i - y(i,j) \right)^2 + \frac{\lambda}{2} \sum_{k=1}^{n} \left( x_k^i \right)^2 $$

Where:
- $r(i,j) = 1$ if user $j$ rated movie $i$, otherwise $r(i,j) = 0$
- $y(i,j)$ is the rating given by user $j$ to movie $i$
- $\lambda$ is the regularization parameter

To learn features for all movies, sum this cost function over all movies:
$$ J(\{x^i\}) = \sum_{i=1}^{m} \left( \sum_{j:r(i,j)=1} \left( w^{(j)} \cdot x^i - y(i,j) \right)^2 + \frac{\lambda}{2} \sum_{k=1}^{n} \left( x_k^i \right)^2 \right) $$

## Combined Cost Function

Finally, combine the cost functions for learning both user parameters ($w$, $b$) and movie features ($x$):
$$ J(\{w^{(j)}, b^{(j)}, x^i\}) = \sum_{i=1}^{m} \sum_{j:r(i,j)=1} \left( w^{(j)} \cdot x^i + b^{(j)} - y(i,j) \right)^2 + \frac{\lambda}{2} \left( \sum_{j=1}^{\nu} \sum_{k=1}^{n} \left( w_k^{(j)} \right)^2 + \sum_{i=1}^{m} \sum_{k=1}^{n} \left( x_k^i \right)^2 \right) $$

## Optimization

Minimize this combined cost function using gradient descent. Update the parameters $w$, $b$, and $x$ iteratively:
1. Update $w$ and $b$:
$$ w^{(j)} := w^{(j)} - \alpha \frac{\partial J}{\partial w^{(j)}} $$
$$ b^{(j)} := b^{(j)} - \alpha \frac{\partial J}{\partial b^{(j)}} $$

2. Update $x$:
$$ x^i := x^i - \alpha \frac{\partial J}{\partial x^i} $$

Where $\alpha$ is the learning rate.

## Conclusion

This collaborative filtering algorithm learns the features of movies from user ratings, enabling predictions even without predefined features. This approach leverages the collaborative nature of user ratings to infer meaningful features and improve recommendation accuracy.

In the next discussion, we'll extend this model to handle binary labels, such as user interactions with items (e.g., likes or favorites).
