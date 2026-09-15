# Logistic Regression using Basic Gradient Descent

Hi guys, this repository is about **Logistic Regression implemented from scratch using the Gradient Descent method** to minimize the loss function.

---

### Mathematical Mechanism Behind the Algorithm

The following steps describe how Logistic Regression learns the optimal weight and bias through Gradient Descent.

#### 1. Initialize the weight and bias

First, we assign initial values to the weight and bias so that the model can start learning. Typically, both are initialized to zero:

$$
w = 0
$$

$$
b = 0
$$

---

#### 2. Compute the linear combination

Next, we compute the **linear combination** for each data point:

$$
z = wx + b
$$

where:

* $x$ is the input feature
* $w$ is the weight
* $b$ is the bias
* $z$ is the linear score

---

#### 3. Apply the Sigmoid Function

The linear score is then passed through the **Sigmoid (Logistic) Function** to convert it into a probability:

$$
\sigma(z) = \frac{1}{1 + e^{-z}}
$$

The output of the sigmoid function is always within the range $(0,1)$, which makes it suitable for representing the probability of the positive class.

Therefore:

$$
\hat{p} = \sigma(z)
$$

where $\hat{p}$ represents the predicted probability that the sample belongs to class 1.

> **Note:** Logistic Regression uses the Sigmoid Function because its output range is $(0,1)$, making it suitable for probability estimation.

---

#### 4. Compute the Loss Function

After obtaining the predicted probability, we calculate the **Binary Cross-Entropy (BCE)** loss, also known as **Log Loss**.

The objective of Logistic Regression is to minimize this loss function:

$$ J(w,b) =-\frac{1}{n}\sum_{i=1}^{n}\left[y_i\log(\hat{p}_i)+(1-y_i)\log(1-\hat{p}_i)\right]$$

where:

* $y_i$ is the actual class
* $\hat{p}_i$ is the predicted probability
* $n$ is the number of training samples

In this formula, $\log$ refers to the **natural logarithm (base $e$)**.

---

#### 5. Compute the Partial Derivatives

Next, we compute the partial derivatives of the loss function with respect to the weight and bias.

For the weight:

$$\frac{\partial J}{\partial w}=\frac{1}{n}\sum_{i=1}^{n}x_i(\hat{p}_i-y_i)$$

For the bias:

$$\frac{\partial J}{\partial b}=\frac{1}{n}\sum_{i=1}^{n}(\hat{p}_i-y_i)$$

These derivatives indicate the **direction and magnitude of the change** needed for the weight and bias to reduce the loss.

---

#### 6. Update the Weight and Bias using Gradient Descent

After calculating the gradients, we update the weight and bias using the **Gradient Descent** algorithm:

$$
w := w-\alpha\frac{\partial J}{\partial w}
$$

$$
b := b-\alpha\frac{\partial J}{\partial b}
$$

where $\alpha$ is the **learning rate**, which controls the size of each update.

---

#### 7. Repeat Until Convergence

With the newly updated weight and bias, we repeat the entire process:

$$
z
\rightarrow
\hat{p}
\rightarrow
Loss
\rightarrow
Gradients
\rightarrow
Update
$$

The algorithm continues until the gradients become sufficiently close to zero, indicating that the model has approximately converged to an optimal solution, or until the maximum number of iterations is reached.

For example, we can define the convergence condition as:

$$
\left|\frac{\partial J}{\partial w}\right| < \epsilon
$$

and

$$
\left|\frac{\partial J}{\partial b}\right| < \epsilon
$$

where $\epsilon$ is a small tolerance value.

---

### Summary of the Algorithm

| Step | Process | Mathematical Expression | Purpose |
| :--- | :--- | :--- | :--- |
| **1** | Initialize Parameters | $w = 0, \quad b = 0$ | Initialize the weight and bias before training |
| **2** | Compute the Linear Combination | $z = wx + b$ | Calculate the linear score for each data point |
| **3** | Apply the Sigmoid Function | $\hat{p} = \sigma(z) = \frac{1}{1 + e^{-z}}$ | Convert the linear score into a probability |
| **4** | Compute Binary Cross-Entropy Loss | $J(w,b) = -\frac{1}{n}\sum_{i=1}^{n}[y_i\log(\hat{p}_i) + (1-y_i)\log(1-\hat{p}_i)]$ | Measure how far the predicted probabilities are from the actual labels |
| **5** | Compute Gradients | $\frac{\partial J}{\partial w} = \frac{1}{n}\sum x_i(\hat{p}_i-y_i)$ <br> $\frac{\partial J}{\partial b} = \frac{1}{n}\sum(\hat{p}_i-y_i)$ | Determine the direction and magnitude for updating the parameters |
| **6** | Update Parameters | $w := w - \alpha\frac{\partial J}{\partial w}$ <br> $b := b - \alpha\frac{\partial J}{\partial b}$ | Move the parameters toward values that reduce the loss |
| **7** | Check Convergence | $\left\|\frac{\partial J}{\partial w}\right\| < \epsilon$ và $\left\|\frac{\partial J}{\partial b}\right\| < \epsilon$ | Check whether the model has sufficiently converged |
| **8** | Repeat the Process | $z \rightarrow \hat{p} \rightarrow J \rightarrow \text{Gradients} \rightarrow \text{Update}$ | Repeat the learning process until convergence or the maximum number of iterations is reached |

