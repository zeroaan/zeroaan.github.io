---
layout: post
title:  "[ML] 카이제곱검정(chi-squared test)"
date:   2020-06-03 12:31:18
author: zeroaan
categories: ml/dl
use_math: true
# tags: python code
# cover:  "/assets/header_image.jpg"
---

### 카이제곱 검정 (교차분석)


```python
import pandas as pd

남 = [82, 53, 15, 5]
여 = [6, 27, 41, 75]
df = pd.DataFrame([남, 여], columns=['기계공학과', '경영학과', '화학과', '간호학과'], index=['남', '여'])
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>기계공학과</th>
      <th>경영학과</th>
      <th>화학과</th>
      <th>간호학과</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>남</th>
      <td>82</td>
      <td>53</td>
      <td>15</td>
      <td>5</td>
    </tr>
    <tr>
      <th>여</th>
      <td>6</td>
      <td>27</td>
      <td>41</td>
      <td>75</td>
    </tr>
  </tbody>
</table>
</div>



- 귀무가설 : 성별에 따라 학과에 차이가 없다.<br>
- 대립가설 : 성별에 따라 학과에 차이가 있다.


```python
from scipy.stats import chi2_contingency
print('p-value:', chi2_contingency(df)[1])
```

    p-value: 9.842014607546535e-32
    

P-value가 0.05 보다 작으므로 대립가설이 채택된다.

즉, 성별에 따라 학과에 차이가 있다고 볼 수 있다.

<br><br><br>

### 타이타닉 데이터를 이용하여 카이제곱검정을 해보겠다.


```python
import seaborn as sns
titanic = sns.load_dataset('titanic')
titanic
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>survived</th>
      <th>pclass</th>
      <th>sex</th>
      <th>age</th>
      <th>sibsp</th>
      <th>parch</th>
      <th>fare</th>
      <th>embarked</th>
      <th>class</th>
      <th>who</th>
      <th>adult_male</th>
      <th>deck</th>
      <th>embark_town</th>
      <th>alive</th>
      <th>alone</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>7.2500</td>
      <td>S</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>71.2833</td>
      <td>C</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>C</td>
      <td>Cherbourg</td>
      <td>yes</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>3</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>7.9250</td>
      <td>S</td>
      <td>Third</td>
      <td>woman</td>
      <td>False</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>53.1000</td>
      <td>S</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>C</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>8.0500</td>
      <td>S</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>True</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>886</th>
      <td>0</td>
      <td>2</td>
      <td>male</td>
      <td>27.0</td>
      <td>0</td>
      <td>0</td>
      <td>13.0000</td>
      <td>S</td>
      <td>Second</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>True</td>
    </tr>
    <tr>
      <th>887</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>19.0</td>
      <td>0</td>
      <td>0</td>
      <td>30.0000</td>
      <td>S</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>B</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>888</th>
      <td>0</td>
      <td>3</td>
      <td>female</td>
      <td>NaN</td>
      <td>1</td>
      <td>2</td>
      <td>23.4500</td>
      <td>S</td>
      <td>Third</td>
      <td>woman</td>
      <td>False</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>False</td>
    </tr>
    <tr>
      <th>889</th>
      <td>1</td>
      <td>1</td>
      <td>male</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>30.0000</td>
      <td>C</td>
      <td>First</td>
      <td>man</td>
      <td>True</td>
      <td>C</td>
      <td>Cherbourg</td>
      <td>yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>890</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>32.0</td>
      <td>0</td>
      <td>0</td>
      <td>7.7500</td>
      <td>Q</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Queenstown</td>
      <td>no</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
<p>891 rows × 15 columns</p>
</div>



<br><br><br>

성별에 따라 생존여부가 차이가 있는지 알아보자.


```python
df2 = pd.crosstab(titanic.survived, titanic.sex)
df2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>sex</th>
      <th>female</th>
      <th>male</th>
    </tr>
    <tr>
      <th>survived</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>81</td>
      <td>468</td>
    </tr>
    <tr>
      <th>1</th>
      <td>233</td>
      <td>109</td>
    </tr>
  </tbody>
</table>
</div>



- 귀무가설 : 성별에 따라 생존여부 차이가 없다.
- 대립가설 : 성별에 따라 생존여부 차이가 있다.


```python
print('p-value:', chi2_contingency(df2)[1])
```

    p-value: 1.1973570627755645e-58
    

P-value가 0.05 보다 작으므로 대립가설이 채택된다.

즉, 성별에 따라 생존여부 차이가 있다고 볼 수 있다.

<br><br><br>

클래스별 생존여부가 차이가 있는지 알아보자.


```python
df3 = pd.crosstab(titanic.survived, titanic.pclass)
df3
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>pclass</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
    </tr>
    <tr>
      <th>survived</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>80</td>
      <td>97</td>
      <td>372</td>
    </tr>
    <tr>
      <th>1</th>
      <td>136</td>
      <td>87</td>
      <td>119</td>
    </tr>
  </tbody>
</table>
</div>



- 귀무가설 : 클래스에 따라 생존여부 차이가 없다.
- 대립가설 : 클래스에 따라 생존여부 차이가 있다.


```python
print('p-value:', chi2_contingency(df3)[1])
```

    p-value: 4.549251711298793e-23
    

P-value가 0.05 보다 작으므로 대립가설이 채택된다.

즉, 클래스에 따라 생존여부 차이가 있다고 볼 수 있다.
