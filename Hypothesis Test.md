### Hypothesis Testing

#### Definition
Hypothesis Testing (also called a Significance Test) is a statistical method used to determine whether the difference between treatments is real or caused by randomness.

It helps us decide whether an observed result is meaningful or simply due to natural variation.

---

#### Why Do We Use It?

- Humans tend to see patterns in randomness.
- Random variation can create misleading differences.
- We need a structured way to determine whether a difference is real or due to chance.
- It protects us from being fooled by unusual but random behavior.

---

#### Core Concept

We start by assuming there is **no real difference** between groups.  
Then we test whether the observed difference is too extreme to be explained by chance.

If the result is very unlikely under randomness → we reject the assumption.

---

#### Types of Hypotheses

##### 1) Null Hypothesis (H₀)

The Null Hypothesis is the default assumption.

It states:
There is no real difference between groups.
Any observed difference is due to chance.

Example:

H₀: A = B

Meaning: Treatment A and Treatment B are equivalent.

---

##### 2) Alternative Hypothesis (H₁ or Ha)

The Alternative Hypothesis states that a real difference exists.

Examples:

H₁: A ≠ B  
H₁: B > A

---

#### Types of Hypothesis Tests

##### 1) One-Tail (One-Way) Test

Used when we care about only one direction.

Example:

H₁: B > A

- Tests improvement in one direction only.
- Extreme results in one direction count toward the p-value.
- Common in A/B testing when A is the default option.

---

##### 2) Two-Tail (Two-Way) Test

Used when we care about differences in both directions.

Example:

H₁: A ≠ B

- Tests for any difference (better or worse).
- Extreme results in both directions count toward the p-value.
- More conservative.
- Most statistical software uses this by default.

---

#### Final Summary

Hypothesis testing is a structured method that prevents us from misinterpreting random variation as meaningful differences.

We assume no real difference (H₀) and only conclude that a difference exists if strong statistical evidence supports it.