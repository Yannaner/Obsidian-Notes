#### Overview

feature scaling: a technique used to standardize the range of independent variables or features of data. Feature scaling helps to make gradient descent work more efficiently.

#### Key Points

1. **Feature Size and Parameter Values**
    
    - Example features: $x_1$ (size of the house in square feet) and $x_2$ (number of bedrooms).
    - $x_1$ ranges from 300 to 2000 square feet.
    - $x_2$ ranges from 0 to 5 bedrooms.
2. **Impact on Parameter Values**
    
    - Example house: 2000 square feet, 5 bedrooms, priced at $500,000.
    - Parameter values and their impact on the estimated price:
        $$w_1 = 50, w_2 = 0.1, b = 50$$
        
        - Predicted price: $100,050,000 (unrealistic).
	$$w_1 = 0.1, w_2 = 50, b = 50$$
        
        - Predicted price: $500,000 (realistic).
3. **Effect of Feature Size on Parameters**
    
    - Larger feature ranges tend to correspond with smaller parameter values.
    - Smaller feature ranges tend to correspond with larger parameter values.
4. **Gradient Descent Behavior Without Feature Scaling**
    
    - Contour plots with unscaled features form elongated ellipses.
    - Gradient descent may bounce back and forth, converging slowly to the minimum.
5. **Feature Scaling Transformation**
    
    - Transform $x_1$ and $x_2$ to a comparable range, e.g., from 0 to 1.
    - Contour plots with scaled features form more circular shapes.
    - Gradient descent finds a more direct path to the global minimum.
6. **Benefits of Feature Scaling**
    
    - Speeds up gradient descent significantly.
    - Ensures that features contribute proportionately to the cost function.

## Different Feature Scaling Techniques

1. **Feature Scaling Techniques**
    
    - Scaling transforms features to have comparable ranges, improving gradient descent performance.
2. **Simple Scaling by Maximum Value**
    
    - For feature $x_1$ ranging from 300 to 2000, scale by dividing each $x_1$ value by 2000 (maximum value):
        
        
        
        $$x_{1_{scaled}} = \frac{x_1}{2000}$$
        
        - Scaled $x_1$ ranges from 0.15 to 1.
    - For feature $x_2$ ranging from 0 to 5, scale by dividing each $x_2$ value by 5 (maximum value):
        
        
        
        $$x_{2_{scaled}} = \frac{x_2}{5}$$
        
        - Scaled $x_2$ ranges from 0 to 1.
3. **Mean Normalization**
    
    - Center features around zero to have both negative and positive values.
    - Calculate the mean $\mu$ of $x_1$ and $x_2$:
        - For $x_1$ with $\mu_1 = 600$:
            
            
            
            $$x_{1_{normalized}} = \frac{x_1 - \mu_1}{2000 - 300}$$
            
            - Normalized $x_1$ ranges from -0.18 to 0.82.
        - For $x_2$ with $\mu_2 = 2.3$:
            $$x_{2_{normalized}} = \frac{x_2 - \mu_2}{5 - 0}$$
            
            - Normalized $x_2$ ranges from -0.46 to 0.54.
4. **Z-score Normalization**
    
    - Standardize features using mean $\mu$ and standard deviation $\sigma$.
    - For $x_1$ with $\mu_1 = 600$ and $\sigma_1 = 450$:
        
        
        
        $$x_{1_{z-score}} = \frac{x_1 - \mu_1}{\sigma_1}$$
        
        - Z-score normalized $x_1$ ranges from -0.67 to 3.1.
    - For $x_2$ with $\mu_2 = 2.3$ and $\sigma_2 = 1.4$:
        
        
        
        $$x_{2_{z-score}} = \frac{x_2 - \mu_2}{\sigma_2}$$
        
        - Z-score normalized $x_2$ ranges from -1.6 to 1.9.
5. **Practical Guidelines for Feature Scaling**
    
    - Aim to scale features to a range around -1 to 1.
    - If features range slightly outside this range, it's usually acceptable.
    - Features with extremely large or small ranges should be scaled for optimal gradient descent performance.
6. **Examples of Scaling Necessities**
    
    - Feature $x_3$ ranging from -100 to 100 should be scaled to around -1 to 1.
    - Feature $x_4$ ranging from -0.001 to 0.001 should be scaled.
    - Feature $x_5$ (e.g., temperature from 98.6 to 105°F) should be scaled to improve gradient descent speed.
7. **Conclusion on Feature Scaling**
    
    - Feature scaling is beneficial and often necessary for efficient gradient descent.
    - When in doubt, scaling features can help prevent issues with gradient descent convergence.