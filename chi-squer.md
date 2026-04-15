# 📊 Chi-Square Test (A/B Testing)

## 📌 Overview
The **Chi-Square Test** is a statistical method used in A/B testing when dealing with **categorical data** (e.g., Click vs No Click).  
It helps determine whether the observed differences between groups are **statistically significant** or just due to randomness.

---

## 🧪 Example: Testing Headlines

We test three different headlines (A, B, C), each shown to 1000 visitors:

| Headline | Click | No Click | Total |
|----------|-------|----------|-------|
| A        | 14    | 986      | 1000  |
| B        | 8     | 992      | 1000  |
| C        | 12    | 988      | 1000  |

- Total clicks = **34**  
- Total visitors = **3000**

---

## 📌 Expected Values

Assuming **no real difference** between headlines:

- Expected clicks per headline:
  
  `34 / 3 ≈ 11.33`

- Expected no-clicks per headline:
  
  `1000 - 11.33 ≈ 988.67`

---

## 📐 Pearson Residual

To measure the deviation between observed and expected values:
R = (Observed - Expected) / sqrt(Expected)


---

## 📊 Chi-Square Statistic

The Chi-Square value is calculated as:

X^2 = Σ (R^2)

This represents the total deviation across all categories.

---

## 🎯 Degrees of Freedom

Degrees of freedom (df) are calculated as:
df = (rows - 1) * (columns - 1)


### ✅ In this example:
- Rows = 3 (Headlines A, B, C)  
- Columns = 2 (Click / No Click)  


---

## 🧠 Why Degrees of Freedom Matter

- Determines the **shape of the Chi-Square distribution**
- Used to calculate the **p-value**
- Helps decide if the result is **statistically significant**

---

## 🔁 Randomization (Simulation Idea)

To validate results:

1. Shuffle the data randomly  
2. Redistribute clicks across headlines  
3. Recalculate X² multiple times  
4. Compare with the observed X²  

👉 If the observed value is much larger than random values → **Significant**

---

## 🧾 Final Decision

After computing the Chi-Square value:

- Compare with critical value (based on df)  
- Or compute the **p-value**

### 📌 Rule:
- **p-value < 0.05** → Significant difference ✅  
- **p-value ≥ 0.05** → Not significant ❌  

---

```
from scipy.stats import chi2_contingency

contingency_table = pd.crosstab(data['Sex'], data['Survived'])
chi2, p, dof, expected=chi2_contingency(contingency_table)


print('Chi2',chi2,end='\n')
print('p_value',p,end='\n')
print('dof',dof,end='\n')

print('expected',expected,end='\n')
print("H0 is Rejected ?",p<0.05)
```
```
'''output:
Chi2 260.71702016732104
p_value 1.1973570627755645e-58
dof 1
expected [[193.47474747 120.52525253]
 [355.52525253 221.47474747]]
H0 is Rejected ? True'''
```

## 🚀 Summary

- Used for **categorical A/B testing**
- Compares **observed vs expected frequencies**
- Key components:
  - Pearson Residual
  - Chi-Square Statistic
  - Degrees of Freedom
- Helps determine if results are **real or random**


