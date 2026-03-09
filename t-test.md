## T-Test

There are different types of significance tests, and the choice of the test depends on the type of data and how it is measured.

The **t-test** is one of the most commonly used statistical tests. It is named after **Student’s t-distribution**, which was developed by the statistician **W. S. Gosset**.

---

## Test Statistic
A **test statistic** is a numerical value that measures the difference or effect of interest in the data.

---

## T-Statistic
The **t-statistic** is a standardized version of common statistics such as the difference between means.  
It allows us to compare the observed result with a reference distribution.

---

## T-Distribution
The **t-distribution** is a probability distribution derived under the **null hypothesis**.  
The calculated t-statistic is compared with this distribution to determine whether the observed difference is statistically significant.

---

## Significance Testing

All significance tests require a **test statistic** to determine whether the observed difference:

- Falls within the expected range under the **null hypothesis**, or  
- Lies in the **tail of the distribution**, indicating statistical significance.

In a **t-test**, the data is standardized to produce a **t-statistic**, which is then used to calculate the **p-value**.

## Code Example

```python
import pandas as pd
from sklearn.preprocessing import StandardScaler
data=pd.read_csv('train.csv')
df=data.copy()
df['Fare']=StandardScaler().fit_transform(df[['Fare']])

from scipy import stats
p_value=stats.ttest_ind(df[df['Survived']==1]['Fare'],df[df['Survived']==0]['Fare'],equal_var=False)

# p_value =2.6993323503140942e-11 This mean that the p-value ≈ 0 → the probability that this difference occurred by chance is extremely low.
# Therefore, we reject the null hypothesis (H₀).
```