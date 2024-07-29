# Diagnostics for Improving Learning Algorithms

## Importance of Bias and Variance

- **Key Ideas:**
  - Bias and variance are crucial for diagnosing model performance.
  - Error analysis is the second most important diagnostic tool.

## Error Analysis

### Process

1. **Identify Misclassified Examples:**
   - Example: `m_cv = 500` cross-validation examples, 100 misclassified.
   
2. **Group Misclassified Examples:**
   - Identify common themes or traits in misclassified examples.
   - Example Categories:
     - Pharmaceutical spam
     - Deliberate misspellings
     - Unusual email routing
     - Phishing emails
     - Embedded image spam

### Example Analysis

- **Counts:**
  - Pharmaceutical spam: 21 emails
  - Deliberate misspellings: 3 emails
  - Unusual email routing: 7 emails
  - Phishing emails: 18 emails

- **Insights:**
  - Focus on fixing major issues (e.g., pharmaceutical spam, phishing emails).
  - Lower priority for less common issues (e.g., deliberate misspellings).

### Overlapping Categories

- Emails can belong to multiple categories (e.g., pharmaceutical spam with unusual routing).

### Sampling for Larger Sets

- **If too many misclassified examples:**
  - Randomly sample a subset (e.g., 100-200 examples) for analysis.

### Post-Analysis Actions

- **Example:**
  - If pharmaceutical spam is a major issue:
    - Collect more data specific to pharmaceutical spam.
    - Create new features (e.g., specific drug names).
  
- **For Phishing Emails:**
  - Develop features to detect suspicious URLs.
  - Collect more phishing email data.

## Integrating Bias and Variance Analysis with Error Analysis

- **Bias-Variance Analysis:**
  - Helps decide if more data is useful.
  
- **Error Analysis:**
  - Inspires specific improvements (e.g., new features, targeted data collection).

## Limitations of Error Analysis

- **Effective for:**
  - Problems humans are good at (e.g., spam detection).
  
- **Challenging for:**
  - Problems humans struggle with (e.g., predicting ad clicks).

## Conclusion

- **Benefits:**
  - Error analysis helps focus on promising model improvements.
  - Saves time by avoiding less impactful fixes.
  
- **Next Steps:**
  - Explore efficient techniques for adding data to improve model performance.

Conventional Model centric approach: AI = code + data(more focuses on code)
Data-centric approach AI = cpde + data( more focuses on data)

[[Transfer Learning]]