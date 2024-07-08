

#Machinelearning
###### AGI - Artificial general intelligence 
- Using learning algorithm

--- 
##### Usage
- retail, travel, transportation, automotive, materials manufacturing

---
##### What is Machine Learning?
- Gives computers the ability to learn without being explicitly programmed
- Have the patience to play the game itself

##### Two main type of machine learning algorithm
- Supervised learning 
- Unsupervised learning
- recommender systems
- Reinforcement learning

### Regression Supervised Learning
**Introduction to Supervised Learning:**

- Supervised learning is responsible for approximately 99% of the economic value created by machine learning today.
- It involves algorithms learning mappings from input (x) to output (y) by using labeled examples.

**Key Characteristics:**

- **Input-Output Mapping:** Algorithms learn to map inputs to the correct outputs.
- **Labeled Data:** The learning process involves examples that include the correct output labels for given inputs.
- **Prediction Capability:** The algorithm eventually learns to predict the output based solely on new inputs.

**Examples of Supervised Learning Applications:**

1. **Spam Filtering:** Input - email; Output - spam or not spam.
2. **Speech Recognition:** Input - audio clip; Output - text transcript.
3. **Machine Translation:** Input - text in one language; Output - text in another language.
4. **Online Advertising:** Input - ad information and user data; Output - likelihood of user clicking the ad.
5. **Self-Driving Cars:** Input - images and sensor data; Output - positions of other cars.
6. **Manufacturing (Visual Inspection):** Input - image of a product; Output - identification of defects.

**Detailed Example - Housing Price Prediction:**

- **Data Collection:** Plot house size (square feet) vs. price (thousands of dollars).
- **Prediction Process:** The algorithm can fit a line or curve to predict the price of a house based on its size.
- **Choice of Model:** Deciding whether to use a straight line, a curve, or a more complex function depends on the data and the desired accuracy.
**Conclusion:**

- Supervised learning involves training models with labeled data to predict outputs for new inputs.
- It is widely used in various industries, from online advertising to manufacturing, due to its economic impact and practical applications

### Classification Supervised Learning
**Introduction to Classification:**

- Supervised learning involves predicting input-output or X-to-Y mappings.
- Two major types: regression (predicting **numbers**) and classification (predicting **categories**).

**Classification Overview:**

- **Example:** Breast cancer detection system to classify tumors as benign (0) or malignant(dangerous) (1).
- **Dataset:** Tumor sizes labeled as benign (0) or malignant (1).
- **Plotting Data:** Tumor size on the horizontal axis; 0 (benign) or 1 (malignant) on the vertical axis.
	tumor 腫瘤
**Difference from Regression:**

- **Regression:** Predicts infinitely many possible numbers.
- **Classification:** Predicts a small number of possible categories.

**Categories in Classification:**

- Categories can be non-numeric (e.g., cat vs. dog) or numeric (e.g., 0, 1, 2).
- The key is the finite, limited set of possible outputs.

**Using Multiple Inputs:**

- Example expanded to include a second input: patient's age.
- **New Dataset:** Tumor size and patient age with benign (circles) or malignant (crosses) tumors.
- **Prediction:** The algorithm finds a boundary to classify new data points (e.g., tumor likely benign).

**Additional Inputs:**

- More inputs can improve predictions (e.g., tumor thickness, cell size uniformity).
- Classification problems often use multiple inputs for more accurate predictions.

**Recap of Supervised Learning:**

- Maps input X to output Y using labeled data.
- **Regression:** Predicts numbers from infinitely many possibilities.
- **Classification:** Predicts a category from a small set of possible outputs.


### Unsupervised Learning
**Introduction to Unsupervised Learning:**

- Unlike supervised learning, unsupervised learning deals with data that doesn't have associated output labels.

**Understanding Unsupervised Learning:**

- **No Output Labels:** Data is not labeled (e.g., no labels like benign or malignant for tumors).
- **Objective:** <mark style="background: #D2B3FFA6;">Find patterns or structures</mark> in the data without predefined labels.
- **Example:** Given patient data (tumor size and age) without knowing if tumors are benign or malignant, the algorithm identifies patterns on its own.
##### Clustering Algorithms:
---
- A type of unsupervised learning that <mark style="background: #D2B3FFA6;">groups data into clusters.</mark>
- **Example 1: Google News:** Clustering related news articles based on common words (e.g., "panda," "twins," "zoo").
- **Example 2: DNA Data:** Clustering genetic data to identify different types of individuals based on gene expression.
- **Example 3: Market Segmentation:** Grouping customers into segments to better serve their needs (e.g., seeking knowledge, career development, staying updated).
---
**Applications and Examples:**

1. **Google News Clustering:**
    
    - Groups related news articles by finding common words in headlines.
    - No human intervention; algorithm identifies clusters based on word frequency.
2. **Clustering Genetic Data:**
    
    - Uses DNA microarray data (genetic activity of individuals) to group people into different categories based on gene expression.
    - Automatically finds structure in data without predefined labels.
3. **Customer Segmentation:**
    
    - Groups customers into different market segments for targeted services.
    - Helps companies understand and serve different customer motivations (e.g., knowledge seekers, career developers, field-specific updates).

**Summary:**
- **Unsupervised Learning:** Finds patterns and structures in unlabeled data.
- **Clustering:** Groups data into clusters without predefined labels.
- **Applications:** News article grouping, genetic data clustering, customer segmentation.

**Additional Types of Unsupervised Learning:**

1. **Anomaly Detection:**
    - Identifies unusual events or data points.
    - **Application:** Fraud detection in financial systems, identifying unusual transactions as potential fraud.
2. **Dimensionality Reduction:**
    - Compresses large datasets into smaller ones while retaining as much information as possible.
    - Helps simplify and visualize data.
    
Unsupervised learning techniques are essential for discovering hidden patterns in data without predefined labels.

Notes Links:
[[LinearRegressionModel]]
[[Cost Function]]
[[Gradient Descent]]
[[Multiple Features]]
[[Feature Scaling]]