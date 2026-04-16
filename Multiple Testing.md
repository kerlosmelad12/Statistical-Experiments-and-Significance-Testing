## Multiple Testing

When performing statistical tests, we usually deal with **Type I error**:

- **Type I Error (False Positive):**  
  Concluding that an effect is significant when it is actually not.

---

### 🔹 The Problem with Multiple Predictors

If you test multiple predictors (e.g., 20 variables), each test typically uses a significance level:

- \( \alpha = 0.05 \)

This means each individual test has a 5% chance of producing a false positive.

---

### 🔹 Probability of False Positives

If all predictors are actually **not significant**, the probability that a single test correctly shows "non-significant" is:

- \( 1 - \alpha = 0.95 \)

For 20 independent tests:

- Probability that **all tests are non-significant**:
  
  \[
  0.95^{20} \approx 0.36
  \]

- Therefore, the probability that **at least one test appears significant by chance**:

  \[
  1 - 0.95^{20} \approx 0.64
  \]

👉 This means there's a **64% chance** of getting at least one false positive!

---

### 🔹 Alpha Inflation

This phenomenon is called **Alpha Inflation**:

> The more tests you perform, the higher the probability of getting false significant results just by chance.

---

### 🔹 Multiple Comparisons Problem

When comparing multiple groups (e.g., A, B, C), you might ask:

- Is A different from B?
- Is B different from C?
- Is A different from C?

Each additional question is a **new hypothesis test**, which increases the overall chance of making a Type I error.

---

### 🔹 Key Insight

> The more hypotheses you test, the more likely you are to find "significant" results purely by chance — even if no real effect exists.

---

### 🔹 Common Solutions

To control this problem, we use correction methods such as:

- **Bonferroni Correction**
- **False Discovery Rate (FDR)**
- **Holm Method**

These methods adjust the significance level to reduce the risk of false positives.

---