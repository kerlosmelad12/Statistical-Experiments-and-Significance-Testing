# Permutation Test

## Definition
Permutation test is the process of combining two or more samples and randomly reallocating the observations to resamples.

## Why Use It?
Permutation Test is used to determine whether the observed difference between groups is significant or just by chance.  

For example, if you have multiple groups (A, B, C) and a variable like `Age`:

- **Null Hypothesis (H0):**  
- The permutation test helps to check if there is a statistically significant difference among the groups.

## Steps
1. Combine the results from all groups into a single dataset.
2. Shuffle the combined data and randomly draw (without replacement) a resample of the same size as group A.
3. From the remaining data, randomly draw (without replacement) a resample of the same size as group B.
4. Repeat for groups C, D, etc. You now have one set of resamples matching the original sample sizes.
5. Calculate the statistic of interest (e.g., difference in means) for these resamples — this is one permutation iteration.
6. Repeat the steps **R** times to create a permutation distribution of the test statistic.

## Python Code Example (Titanic Dataset)

```python
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
# Read Data
data=pd.read_csv('train.csv')

# Calculate mean age for Survived and Not Survived
MSAGE = np.mean(data[data['Survived'] == 1]['Age'])
MNAGE = np.mean(data[data['Survived'] == 0]['Age'])

# Observed absolute difference
OBSERVED = np.abs(MNAGE - MSAGE)

# Number of samples in each group
n_Supervised = len(data[data['Survived'] == 1])
n_unsupervised = len(data[data['Survived'] == 0])

# Permutation function
def permutation(NS, NUS):
  n = NS + NUS
  idxS = set(np.random.choice(range(n), NS, replace=False))
  idxUS = set(range(n)) - idxS
  return np.abs(np.mean(data.iloc[list(idxUS)]['Age']) - np.mean(data.iloc[list(idxS)]['Age']))

# Generate permutation distribution
diff_values = [permutation(n_Supervised, n_unsupervised) for _ in range(1000)]

# Plot histogram
fig, ax = plt.subplots(figsize=(10, 8))
ax.hist(diff_values, bins=11, rwidth=0.9)
ax.axvline(x=OBSERVED, color='black', lw=2)
ax.text(OBSERVED + 0.5, max(np.histogram(diff_values, bins=11)[0]) * 0.9, 
      'Observed difference', bbox={'facecolor':'white'})
ax.set_xlabel('Age differences')
ax.set_ylabel('Frequency')
ax.set_title('Permutation Test: Age Difference (Survived vs Not Survived)')
plt.show()


