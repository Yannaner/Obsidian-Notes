

# Content-Based Filtering in Recommender Systems

In this video, we will develop a content-based filtering algorithm for recommender systems. We will compare this approach with collaborative filtering, which we've previously explored. Let's dive in.

## Collaborative Filtering vs. Content-Based Filtering

- **Collaborative Filtering**: Recommends items based on the ratings of similar users. Uses user-item interactions to find patterns and make recommendations.
- **Content-Based Filtering**: Recommends items based on the features of users and items. Requires knowledge of user and item features to determine good matches.

### Key Concepts

- **Collaborative Filtering**: Uses user ratings to recommend items. For example, if users A and B have similar ratings, items rated highly by A will be recommended to B.
- **Content-Based Filtering**: Uses features of users and items to recommend items. For example, user preferences (age, gender, country) and item attributes (genre, release year) are used to find good matches.

## Examples of Features

### User Features
- Age
- Gender (one-hot encoded: male, female, unknown)
- Country (one-hot encoded for approximately 200 countries)
- Past behaviors (e.g., ratings of the top 1,000 movies)

### Item Features (e.g., Movies)
- Year of release
- Genre(s)
- Critic reviews
- Average rating by users

## Constructing Feature Vectors

- **User Feature Vector (x_u for user j)**: Aggregates various user features.
- **Item Feature Vector (x_m for movie i)**: Aggregates various item features.

### Example Features

- **User Features**: Age, gender, country, average rating per genre, etc.
- **Item Features**: Year, genre, critic reviews, average user rating, etc.

## Learning to Match Users and Items

In collaborative filtering, we predicted the rating of user j on movie i as:
$$ \hat{y}_{ij} = w_j \cdot x_i + b_j $$

In content-based filtering, we simplify the notation and remove the bias term \( b_j \):
$$ \hat{y}_{ij} = v_{u} \cdot v_{m} $$

### Notation

- **v_u (user vector)**: Represents user preferences.
- **v_m (movie vector)**: Represents item attributes.

### Learning Algorithm

- **v_u**: Computed from user features (e.g., preferences for romance, action genres).
- **v_m**: Computed from item features (e.g., genre composition).

### Example Vectors

- **User Vector**: \( v_u = [4.9, 0.1, \ldots] \) (e.g., preference for romance, action)
- **Movie Vector**: \( v_m = [4.5, 0.2, \ldots] \) (e.g., composition of romance, action genres)

The dot product of these vectors predicts how much the user will like the movie:
$$ \hat{y}_{ij} = v_u \cdot v_m $$

### Challenges

- **Feature Vectors of Different Sizes**: \( x_u \) and \( x_m \) can have different lengths.
- **Consistent Vector Dimensions**: \( v_u \) and \( v_m \) must have the same dimensions to compute the dot product. For example, both could be vectors of 32 numbers.

## Summary

- **Collaborative Filtering**: Uses user-item interactions to make recommendations.
- **Content-Based Filtering**: Uses user and item features to find good matches.
- **Approach**:
