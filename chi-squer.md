# 📊 Chi-Square Test (A/B Testing)

## 📌 Overview

The **Chi-Square Test** is a statistical method used in A/B testing when working with **categorical data**  
(e.g., Click vs No Click, Survived vs Not Survived).

It helps determine whether the differences between groups are:
- **Real (statistically significant)**  
- or just due to **random variation**

---

## 🧪 Example: Testing Headlines

We test three different headlines (A, B, C), each shown to 1000 visitors.

| Headline | Click | No Click | Total |
|----------|-------|----------|-------|
| A        | 14    | 986      | 1000  |
| B        | 8     | 992      | 1000  |
| C        | 12    | 988      | 1000  |

- Total clicks = **34**
- Total visitors = **3000**

---

## 📌 Expected Values

Assuming there is **no difference between headlines**, we distribute clicks evenly:

- Expected clicks per headline:

\[
\frac{34}{3} \approx 11.33
\]

- Expected no-clicks per headline:

\[
1000 - 11.33 \approx 988.67
\]

---

## 📐 Pearson Residual

To measure how far observed values deviate from expected values:

\[
R = \frac{O - E}{\sqrt{E}}
\]

Where:
- \(O\) = Observed value  
- \(E\) = Expected value  

---

## 📊 Chi-Square Statistic

The Chi-Square statistic is computed as:

\[
X^2 = \sum R^2
\]

It measures the **total deviation** between observed and expected frequencies.

---

## 🎯 Degrees of Freedom

Degrees of freedom (df) are calculated as:

\[
df = (\text{rows} - 1) \times (\text{columns} - 1)
\]

### ✅ In this example:
- Rows = 3 (A, B, C)
- Columns = 2 (Click / No Click)

\[
df = (3 - 1)(2 - 1) = 2
\]

---

## 🧠 Why Degrees of Freedom Matter

- Determines the shape of the Chi-Square distribution  
- Used to compute the **p-value**  
- Helps assess statistical significance  

---

## 🔁 Randomization (Simulation Idea)

To validate the test:

1. Shuffle the data randomly  
2. Redistribute clicks across headlines  
3. Recalculate \( X^2 \)  
4. Repeat many times  
5. Compare observed \( X^2 \) with simulated values  

👉 If observed \( X^2 \) is much larger → result is significant

---

## 🧾 Python Implementation

```python
from scipy.stats import chi2_contingency

contingency_table = pd.crosstab(data['Sex'], data['Survived'])

chi2, p, dof, expected = chi2_contingency(contingency_table)

print('Chi2:', chi2)
print('p-value:', p)
print('dof:', dof)
print('expected:\n', expected)

print("Reject H0?", p < 0.05)

Chi2: 260.71702016732104
p_value: 1.1973570627755645e-58
dof: 1

expected:
[[193.47474747 120.52525253]
 [355.52525253 221.47474747]]

H0 is Rejected ? True
