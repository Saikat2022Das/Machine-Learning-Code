# Ridge and Lasso Regularization

Regularization is a technique used in machine learning to prevent overfitting by adding a penalty term to the loss function. Two commonly used regularization methods are **Ridge (L2)** and **Lasso (L1)**.

---

## 📌 1. Mathematical Formulation

### 🔹 Ridge Regression (L2 Regularization)

\[
J(\beta) = \sum_{i=1}^{n} (y_i - \hat{y}_i)^2 + \lambda \sum_{j=1}^{p} \beta_j^2
\]

- Adds **L2 penalty** (squared magnitude of coefficients)
- λ (lambda) or α controls the strength of regularization

---

### 🔹 Lasso Regression (L1 Regularization)

\[
J(\beta) = \sum_{i=1}^{n} (y_i - \hat{y}_i)^2 + \lambda \sum_{j=1}^{p} |\beta_j|
\]

- Adds **L1 penalty** (absolute value of coefficients)
- Encourages sparsity in the model

---

## 📌 2. Effect of Increasing λ (Alpha)

### 🔹 Ridge Regression
- As **λ increases**, coefficients shrink **towards zero**
- However, they **never become exactly zero**
- All features remain in the model (no feature elimination)

---

### 🔹 Lasso Regression
- As **λ increases**, some coefficients become **exactly zero**
- This effectively removes features from the model

---

## 📌 3. Dimensionality Reduction

Because Lasso sets some coefficients to zero:

- It performs **automatic feature selection**
- Reduces model complexity
- Can be used as a **dimensionality reduction technique**

Ridge, on the other hand:
- Only shrinks coefficients
- Does **not eliminate features**

---

## 📌 4. Why Lasso Produces Zero Coefficients

The key reason lies in the **geometry of the penalty**:

### 🔹 Ridge (L2)
- Penalty forms a **circular constraint**
- Solution rarely touches axes → coefficients shrink but remain non-zero

---

### 🔹 Lasso (L1)
- Penalty forms a **diamond-shaped constraint**
- Corners lie on axes → optimization often hits these corners
- This forces some coefficients to become **exactly zero**

---

### 🔹 Intuition

- L1 penalty applies a **constant shrinkage force**
- When λ is large, this force is strong enough to:
  - completely eliminate weak features
- Hence, coefficients become **exactly zero**

---

## 📌 5. Summary

| Feature | Ridge (L2) | Lasso (L1) |
|--------|-----------|-----------|
| Penalty | Squared (β²) | Absolute (|β|) |
| Coefficients | Shrink toward zero | Can become zero |
| Feature Selection | ❌ No | ✔ Yes |
| Use Case | Multicollinearity | Sparse models |

---

## 🚀 Key Takeaway

- **Ridge** → good for reducing variance  
- **Lasso** → good for feature selection and dimensionality reduction  
