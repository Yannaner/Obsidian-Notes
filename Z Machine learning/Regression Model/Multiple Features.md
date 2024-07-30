**Overview:** Multiple Linear Regression extends the basic linear regression model by considering multiple input features to predict the output. This allows for more complex and accurate predictions.

**Summary:**

1. **Definition:** Multiple Linear Regression predicts an output using multiple input features. The model is expressed as:
 
    
    $$ f_{w,b}(X) = w_1 x_1 + w_2 x_2 + w_3 x_3 + \ldots + w_n x_n + b $$
    
2. **Example:** For predicting house prices, the model might include features like size ($X_1$), number of bedrooms ($X_2$), number of floors ($X_3$), and age of the house ($X_4$):

    $$ f_{w,b}(X) = 0.1X_1 + 4X_2 + 10X_3 - 2X_4 + 80 $$
    
3. **Interpretation of Parameters:**
    
    - $b = 80$: Base price of the house starts at $80,000.
    - $0.1X_1$: For every additional square foot, the price increases by $100.
    - $4X_2$: For each additional bedroom, the price increases by $4,000.
    - $10X_3$: For each additional floor, the price increases by $10,000.
    - $-2X_4$: For each additional year of the house's age, the price decreases by $2,000.
4. **Vector Notation:**
    
    - Define $\mathbf{W}$ as a vector of parameters:
       
    $$ \mathbf{W} = [w_1, w_2, \ldots, w_n] $$
        
    - Define $\mathbf{X}$ as a vector of features:
    
        $$ \mathbf{X} = [x_1, x_2, \ldots, x_n] $$
        
5. **Compact Form using Dot Product:** The model can be succinctly written as:

    $$ f(\mathbf{X}) = \mathbf{W} \cdot \mathbf{X} + b $$
    
    Where the dot product is:

    $$ \mathbf{W} \cdot \mathbf{X} = w_1 x_1 + w_2 x_2 + \ldots + w_n x_n $$

6. **Terminology:**
    
    - **Multiple Linear Regression**: Model with multiple input features.
    - **Univariate Regression**: Model with a single input feature.

**Key Points:**

- **Multiple Features:** Allows the model to utilize more information for better predictions.
- **Parameter Interpretation:** Each parameter $w_i$ represents the contribution of the corresponding feature $x_i$ to the output.
- **Compact Notation:** Using vector notation and dot product simplifies the representation and computation of the model.
[[Vectorization]]