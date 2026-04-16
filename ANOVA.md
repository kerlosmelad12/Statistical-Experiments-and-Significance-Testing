## ANOVA (Analysis of Variance)

**ANOVA** is a statistical test used to compare the means of **multiple groups** (e.g., A, B, C, D).

- Unlike a **t-test** (which compares only two groups), ANOVA can handle **more than two treatments** at once.
- It tests whether there is **any significant difference among group means**.

---

## 🔹 Key Concepts

### 1. Pairwise Comparison
- A hypothesis test between **two groups** at a time.
- Example:
  - A vs B  
  - B vs C  
  - A vs C  

⚠️ Problem: Performing many pairwise tests increases the risk of **Type I error (alpha inflation)**.

---

### 2. Omnibus Test
- A **single global hypothesis test**.
- Checks whether **at least one group mean is different** from the others.

- Hypotheses:
  - \( H_0 \): All group means are equal  
  - \( H_1 \): At least one mean is different  

👉 ANOVA is an **omnibus test**.

---

### 3. Decomposition of Variance
ANOVA works by splitting total variability into components:

- **Between-group variance (Treatment variance)**  
  Differences between group means and the grand mean  

- **Within-group variance (Error variance)**  
  Variability inside each group  

---

### 4. Sum of Squares (SS)
- Measures total variability as squared deviations:

Types:
- **SS Total (SST)**: Total variation from the grand mean  
- **SS Between (SSB)**: Variation due to treatments  
- **SS Within (SSW)**: Variation due to random error  

---

### 5. F-Statistic
- Measures how large the between-group variation is relative to within-group variation:

\[
F = \frac{MS_{\text{treatment}}}{MS_{\text{error}}}
\]

Where:
- \( MS = \frac{SS}{df} \) (Mean Square)

👉 Interpretation:
- Large F → strong evidence that group means differ  
- Small F → differences likely due to chance  

---

## 🔹 Example Dataset (Stickiness in Seconds)

| Page 1 | Page 2 | Page 3 | Page 4 |
|--------|--------|--------|--------|
| 164    | 172    | 177    | 156    |
| 195    | 178    | 191    | 182    |
| 185    | 177    | 185    | 175    |
| 193    | 171    | 163    | 176    |
| 176    | 155    | 166    | 164    |

- **Grand Mean = 173.75**

---

## 🔹 Why Not Just Pairwise Testing?

If we compare:
- Page 1 vs Page 2  
- Page 1 vs Page 3  
- Page 1 vs Page 4  
- Page 2 vs Page 3  
- Page 2 vs Page 4  
- Page 3 vs Page 4  

👉 This leads to **multiple testing problem** and increases false positives.

✔️ ANOVA solves this by doing **one overall test first**.

---

## 🔹 Permutation-Based ANOVA (Intuition / Algorithm)

Instead of relying only on formulas, we can simulate the null hypothesis:

### Steps:

1. **Combine all data into one pool**  
   (Ignore group labels)

2. **Shuffle the data randomly**

3. **Split into groups**  
   (e.g., 4 groups × 5 values each)

4. **Compute the mean of each group**

5. **Compute variance among group means**  
   (this is the simulated treatment variance)

6. **Repeat steps (2–5) many times**

---

### 🔹 Goal

- Compare:
  - **Observed variance** (from real data)  
  - **Resampled variance** (from shuffled data)

👉 If observed variance is much larger → evidence against \( H_0 \)

---

## 🔹 Key Insight

> ANOVA tests whether differences between groups are **real** or just due to **random variation**.

- It avoids repeated pairwise testing  
- Controls **Type I error** better  
- Uses the **F-statistic** to quantify differences  

---

## 🔹 Applying ANOVA on the Dataset

We used ANOVA to test whether the **mean Age differs across Embarked groups** (C, Q, S).

### 📌 Code

```python
from scipy.stats import f_oneway

group_C = data[data['Embarked'] == 'C']['Age'].dropna()
group_Q = data[data['Embarked'] == 'Q']['Age'].dropna()
group_S = data[data['Embarked'] == 'S']['Age'].dropna()

f_stat, p_value = f_oneway(group_C, group_Q, group_S)

print("F-statistic:", f_stat)
print("p-value:", p_value)