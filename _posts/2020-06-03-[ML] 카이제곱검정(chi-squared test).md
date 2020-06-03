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

![chi_01]({{site.baseurl}}/img/chi_01.png)

<br>

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

![chi_02]({{site.baseurl}}/img/chi_02.png)

<br><br><br>

성별에 따라 생존여부가 차이가 있는지 알아보자.


```python
df2 = pd.crosstab(titanic.survived, titanic.sex)
df2
```

![chi_03]({{site.baseurl}}/img/chi_03.png)

<br>

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

![chi_04]({{site.baseurl}}/img/chi_04.png)

<br>

- 귀무가설 : 클래스에 따라 생존여부 차이가 없다.
- 대립가설 : 클래스에 따라 생존여부 차이가 있다.


```python
print('p-value:', chi2_contingency(df3)[1])
```

    p-value: 4.549251711298793e-23
    

P-value가 0.05 보다 작으므로 대립가설이 채택된다.

즉, 클래스에 따라 생존여부 차이가 있다고 볼 수 있다.
