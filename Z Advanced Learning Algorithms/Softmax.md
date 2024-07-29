# Softmax Regression Algorithm

The softmax regression algorithm is a generalization of logistic regression, which is a binary classification algorithm, to the multiclass classification context. Let's take a look at how it works.

## Logistic Regression Recap
Recall that logistic regression applies when $y$ can take on two possible output values, either $0$ or $1$. The way it computes this output is:
1. First calculate $z = w \cdot x + b$.
2. Then compute $a = g(z)$, where $g$ is the sigmoid function applied to $z$.

We interpret $a$ as logistic regression's estimate of the probability of $y$ being equal to $1$ given those input features $x$.

### Quick Quiz Question
If the probability of $y = 1$ is $0.71$, then what is the probability that $y = 0$? The probabilities must add up to $1$. So, if there's a $71\%$ chance of it being $1$, there has to be a $29\%$ or $0.29$ chance of it being equal to $0$.

### Embellishing Logistic Regression
To set us up for the generalization to softmax regression, let's think of logistic regression as computing two numbers:
1. $a_1$, the chance of $y$ being equal to $1$ given $x$.
2. $a_2$, which is $1 - a_1$, the chance of $y$ being equal to $0$ given $x$.

So, $a_1$ and $a_2$ have to add up to $1$.

## Generalizing to Softmax Regression
Let's now generalize this to softmax regression with a concrete example where $y$ can take on four possible outputs, $1, 2, 3$, or $4$.

### Softmax Regression Computation
1. Compute:
   - $z_1 = w_1 \cdot x + b_1$
   - $z_2 = w_2 \cdot x + b_2$
   - $z_3 = w_3 \cdot x + b_3$
   - $z_4 = w_4 \cdot x + b_4$

   Here, $w_1, w_2, w_3, w_4$ as well as $b_1, b_2, b_3, b_4$ are the parameters of softmax regression.

2. Compute:
   - $a_1 = \frac{e^{z_1}}{e^{z_1} + e^{z_2} + e^{z_3} + e^{z_4}}$
   - $a_2 = \frac{e^{z_2}}{e^{z_1} + e^{z_2} + e^{z_3} + e^{z_4}}$
   - $a_3 = \frac{e^{z_3}}{e^{z_1} + e^{z_2} + e^{z_3} + e^{z_4}}$
   - $a_4 = \frac{e^{z_4}}{e^{z_1} + e^{z_2} + e^{z_3} + e^{z_4}}$

   We interpret $a_1$ as the algorithm's estimate of the chance of $y$ being equal to $1$ given the input features $x$, and similarly for $a_2, a_3$, and $a_4$.

### Quick Quiz
If running softmax regression on a new input $x$ results in:
- $a_1 = 0.30$
- $a_2 = 0.20$
- $a_3 = 0.15$

What is $a_4$? The probabilities must add up to $1$, so $a_4 = 0.35$ ($1 - 0.3 - 0.2 - 0.15$).

## General Case for Softmax Regression
In the general case, $y$ can take on $n$ possible values, $1, 2, 3, \ldots, n$. Softmax regression will compute $z_j = w_j \cdot x + b_j$, where the parameters are $w_1, w_2, \ldots, w_n$, and $b_1, b_2, \ldots, b_n$. 

Finally, we compute:
- $a_j = \frac{e^{z_j}}{\sum_{k=1}^{n} e^{z_k}}$

   $a_j$ is interpreted as the model's estimate that $y$ is equal to $j$ given the input features $x$. By construction, $a_1, a_2, \ldots, a_n$ will always add up to $1$.

### Logistic Regression as a Special Case
It turns out that if you apply softmax regression with $n = 2$, it ends up computing basically the same thing as logistic regression.

## Cost Function for Softmax Regression
Recall for logistic regression:
1. $z = w \cdot x + b$
2. $a_1 = g(z)$ interpreted as $P(y=1)$, and $a_2 = 1 - a_1 = P(y=0)$

The loss for logistic regression was:
$$text{Loss} = -y \log(a_1) - (1 - y) \log(a_2)$$

For softmax regression:
$text{Loss} = -\log(a_j) \text{ if } y = j$

The cost function is the average loss over the entire training set.

```python
def my_softmax(z):
    ez = np.exp(z)              #element-wise exponenial
    sm = ez/np.sum(ez)
    return(sm)
```
```python
model = Sequential(
    [ 
        Dense(25, activation = 'relu'),
        Dense(15, activation = 'relu'),
        Dense(4, activation = 'softmax')    # < softmax activation here
    ]
)
model.compile(
    loss=tf.keras.losses.SparseCategoricalCrossentropy(),
    optimizer=tf.keras.optimizers.Adam(0.001),
)

model.fit(
    X_train,y_train,
    epochs=10
)

```