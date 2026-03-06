# Statistical Significance and p-Values – Summary

## 1. Statistical Significance

Statistical significance is used to determine whether an observed result in an experiment is likely due to a real effect or simply due to random chance.

If a result is **outside the normal range of chance variation**, it is considered **statistically significant**.

Purpose:

* To check if the observed difference is real.
* To avoid being misled by random variation.

---

# Key Concepts

## 2. p-value

The **p-value** measures how extreme the observed result is under the assumption that the **null hypothesis (H0)** is true.

Definition:

> The probability of obtaining results as extreme as the observed results, assuming the null hypothesis is true.

Interpretation:

| p-value  | Meaning                       |
| -------- | ----------------------------- |
| p ≤ 0.05 | Statistically significant     |
| p > 0.05 | Not statistically significant |

Important note:

* A p-value **does NOT mean the probability that the hypothesis is true.**
* It only measures compatibility between the **data and the null hypothesis model.**

---

## 3. Alpha (α)

Alpha is the **threshold used to determine statistical significance**.

Common alpha values:

| Alpha | Meaning                             |
| ----- | ----------------------------------- |
| 0.05  | 5% significance level (most common) |
| 0.01  | stricter test                       |

Decision rule:

If

p-value ≤ α

→ Reject Null Hypothesis

If

p-value > α

→ Fail to Reject Null Hypothesis

Alpha must be **chosen before the experiment**.

---

# Example: Ecommerce Experiment

Two prices were tested:

| Outcome       | Price A | Price B |
| ------------- | ------- | ------- |
| Conversion    | 200     | 182     |
| No Conversion | 23,539  | 22,406  |

Conversion Rates:

Price A:

200 / 23739 = 0.8425%

Price B:

182 / 22588 = 0.8057%

Difference:

0.0368%

Even though **Price A appears slightly better**, we need to check if the difference is statistically significant.



# p-value Controversy

The p-value has been widely criticized because researchers often misuse it.

Common misconceptions:

❌ "p-value is the probability that the hypothesis is true."

❌ "Small p-value proves the hypothesis."

Correct interpretation:

✔ It measures how incompatible the data are with the null hypothesis.

The **American Statistical Association (ASA)** issued guidelines explaining correct usage.

Key principles:

1. P-values show incompatibility with a model.
2. They do NOT measure probability of a hypothesis being true.
3. Decisions should not rely solely on p-values.
4. Transparency and full reporting are important.
5. p-values do not measure effect size.
6. p-values alone are not strong evidence.

---

# Practical Significance

Statistical significance does **not necessarily mean practical importance**.

Example:

With a very large dataset:

Even a **tiny difference** can become statistically significant.

But that difference may have **no real-world impact**.

Therefore:

Always evaluate both:

* Statistical significance
* Practical significance

---

# Type 1 and Type 2 Errors

## Type 1 Error (False Positive)

Rejecting the null hypothesis when it is actually true.

Meaning:

We believe an effect exists, but it is only due to random chance.

Probability:

α (alpha)

---

## Type 2 Error (False Negative)

Failing to reject the null hypothesis when a real effect exists.

Meaning:

We miss detecting a real effect.

This often occurs when:

* Sample size is too small
* Data variability is high

---

# Role of p-values in Data Science

In data science, p-values are mainly used as:

* A diagnostic metric
* A feature selection tool
* A statistical signal indicator

They should **not be the only decision criterion**.

Other factors should also be considered:

* Effect size
* Business impact
* Model performance
* Domain knowledge

---
