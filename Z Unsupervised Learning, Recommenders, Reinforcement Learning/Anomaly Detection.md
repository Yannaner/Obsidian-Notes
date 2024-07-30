# Anomaly Detection Algorithm

[[Feature choosing]]

## Key Concepts
- **Anomaly Detection**: Identifies unusual or anomalous events in an unlabeled dataset of normal events.
- **Example**: Detecting problems in newly manufactured aircraft engines using features like heat (x1) and vibration intensity (x2).

## Methodology
1. **Data Collection**:
   - Collect features (x1, x2, ...) from a set of normal engines (e.g., m engines).

2. **Anomaly Detection Process**:
   - **Model Building**: Create a model to estimate the probability distribution \( p(x) \) of the feature values.
     - High probability regions indicate normal behavior.
     - Low probability regions indicate potential anomalies.
   - **Testing**: For a new engine, compute the feature vector \( X_{\text{test}} \) and estimate \( p(X_{\text{test}}) \).
     - If \( p(X_{\text{test}}) \) is less than a threshold \( <mark style="background: #D2B3FFA6;">epsilon</mark>), flag it as an anomaly.

3. **Density Estimation**:
   - **Training Set**: Use the training data to estimate regions of high and low probability.
   - **Probability Calculation**: Determine the likelihood of new data points using the learned probability distribution.

## Applications
1. **Manufacturing**:
   - Detecting defective parts in aircraft engines, circuit boards, smartphones, etc.
   - Identify anomalous behavior in manufacturing units before shipping.

2. **Fraud Detection**:
   - Detecting unusual user activity or transactions on websites and financial platforms.
   - Examples of features: login frequency, transaction counts, typing speed.
   - Implement additional security checks for flagged anomalies.

3. **IT Infrastructure Monitoring**:
   - Monitoring servers and data centers for unusual behavior.
   - Features: memory usage, CPU load, disk access rates.
   - Flag and investigate anomalies to detect potential hardware failures or security breaches.

4. **Telecommunications**:
   - Monitoring cell towers for unusual behavior to ensure consistent service quality.
   - Anomalies could indicate hardware issues requiring technician intervention.

## Practical Example
- **Aircraft Engines**: 
  - Collect data on normal engines.
  - Model the probability distribution of heat and vibration features.
  - For new engines, compute and compare \( p(X_{\text{test}}) \) with the threshold \( \epsilon \) to detect anomalies.

## Conclusion
- Anomaly detection is a widely used technique in various fields, including manufacturing, finance, IT, and telecommunications.
- Effective in identifying unusual patterns that could indicate defects, fraud, or failures.
- Requires modeling the probability distribution of normal data and comparing new data points against this model.

## Next Steps
- Learn how to use Gaussian distributions to model the data \( p(x) \) for anomaly detection.

[[Gaussian Distribution]]
