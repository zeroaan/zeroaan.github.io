---
layout: post
title:  "[ML] t-검정(t-test), Mann-Whitney U test"
date:   2020-06-03 21:39:04
author: zeroaan
categories: ml/dl
use_math: true
# tags: python code
# cover:  "/assets/header_image.jpg"
---

### t-검정
집단간의 (평균치) 차이를 분석하고자 하는 경우 사용하는 기법이다.

#### t-검정
- 단일표본 t-검정(one sample t-test)
- 독립표본 t-검정(independent two sample t-test)
- 대응표본 t-검정(paired sample t-test)

<br>

#### 1) 단일표본 t-검정
: 단일 집단에서 평균에 대한 가설을 검정하기 위해 사용한다.


```python
from scipy.stats import ttest_1samp

data = [33, 41, 48, 12, 28, 34, 45, 24, 29, 26]

value = 40
```

- 귀무가설 : 10개의 데이터를 통해, 평균이 40이라는 것을 증명한다.
- 대립가설 : 10개의 데이터를 통해, 평균이 40이 아니라는 것을 증명한다.


```python
print("p-value:", ttest_1samp(data, value)[1])
```

    p-value: 0.04274593114073754
    

p-value가 0.05보다 작으므로 대립가설이 채택된다.

즉, 이 데이터의 평균은 40이 아니라고 할 수 있다.

<br><br><br>

### 타이타닉 데이터를 이용하여 단일표본 t-검정을 해보겠다.


```python
import seaborn as sns
titanic = sns.load_dataset('titanic')
titanic
```

![ttest_01]({{site.baseurl}}/img/ttest_01.png)

<br>

타이타닉호에 탑승한 고객 나이의 평균은 약 30세로 알려져 있다

- 귀무가설 : 타이타닉호의 고객 평균 나이는 약 30세라는 것을 증명한다.
- 대립가설 : 타이타닉호의 고객 평균 나이는 약 30세가 아니라는 것을 증명한다.

나이의 값에 결측치가 존재하여 결측치 행을 제거해주었다.


```python
titanic = titanic[titanic['age'].notnull()]
titanic
```

![ttest_02]({{site.baseurl}}/img/ttest_02.png)

<br>

```python
print("p-value:", ttest_1samp(titanic.age, 30)[1])
```

    p-value: 0.5801231230388639
    

p-value가 0.05보다 크므로 귀무가설이 채택된다.

즉, 타이타닉호의 고객 평균 나이는 약 30세라고 할 수 있다.

<br>

#### 2) 독립표본 t-검정
: 서로 무관한 독립된 두 집단의 평균 차이를 검정하는 기법이다.

독립표본 t-검정은 두 집단에 대해 검정을 하기 때문에 독립성, 정규성, 등분산성을 만족해야한다.

<br>

예를 들어 학과에 따라 토익점수가 차이가 있는지에 대해 알아보겠다.<br>
아래 데이터는 A학과의 토익점수, B학과의 토익점수이다.

먼저 정규성을 만족하는지 확인해본다.


```python
from scipy.stats import shapiro

A = [880, 630, 710, 720, 810, 610, 690, 730, 770, 820, 850, 640, 790, 800, 680]
B = [510, 660, 740, 740, 790, 690, 590, 540, 810, 630, 620, 560, 600, 760, 650]

print("A학과의 p-value:", shapiro(A)[1], "\nB학과의 p-value:", shapiro(B)[1])
```

    A학과의 p-value: 0.7938970923423767 
    B학과의 p-value: 0.7592638731002808
    

두 데이터 모두 p-value가 0.05보다 크므로 정규성을 만족한다.

<br>

다음으로 등분산성을 검정한다.


```python
from scipy.stats import levene

print("p-value:", levene(A, B)[1])
```

    p-value: 0.7015345338511132
    

p-value가 0.05보다 크므로 등분산성을 만족한다.

<br>

- 귀무가설 : 학과에 따라 토익점수 차이가 없다.
- 대립가설 : 학과에 따라 토익점수 차이가 있다.


```python
from scipy.stats import ttest_ind

print("p-value:", ttest_ind(A, B)[1])
```

    p-value: 0.01583696690753051
    

p-value가 0.05보다 작으므로 대립가설이 채택된다.

즉, 학과에 따라 토익점수 차이가 있다라고 할 수 있다.

<br><br><br>

### 붓꽃 데이터를 이용하여 단일표본 t-검정을 해보겠다.
(위와 같은 타이타닉 데이터로 해보려 했으나 정규성을 만족하지 못해 할 수 없었음)


```python
import seaborn as sns
iris = sns.load_dataset('iris')
iris
```

![ttest_03]({{site.baseurl}}/img/ttest_03.png)

<br>

종에 따라 꽃받침 길이가 차이가 있는지 보자.


```python
setosa_len = iris.sepal_length[(iris.species == 'setosa')]
virginica_len = iris.sepal_length[(iris.species == 'virginica')]
```


```python
print("setosa의 p-value:", shapiro(setosa_len)[1], "\nvirginica의 p-value:", shapiro(virginica_len)[1])
```

    setosa의 p-value: 0.4595281183719635 
    virginica의 p-value: 0.25832483172416687
    

두 종 모두 p-value가 0.05 이상이므로 정규성을 만족한다.

<br>

다음으로 등분산성을 검정한다.


```python
print("p-value:", levene(setosa_len, virginica_len)[1])
```

    p-value: 0.0010271363228426178
    

p-value가 0.05보다 작으므로 등분산성을 만족하지 못한다.

<br>

등분산성을 만족하지 못할 경우에는 equal_var=False 옵션을 입력하여 t-검정을 진행한다.

- 귀무가설 : 붓꽃 종류에 따라 꽃받침 길이의 차이가 없다.
- 대립가설 : 붓꽃 종류에 따라 꽃받침 길이의 차이가 있다.


```python
print("p-value:", ttest_ind(setosa_len, virginica_len, equal_var=False)[1])
```

    p-value: 3.9668672709859296e-25
    

p-value가 0.05보다 작으므로 대립가설이 채택된다.

즉, 붓꽃 종류에 따라 꽃받침 길이는 차이가 있다라고 할 수 있다.

<br>

#### 3) 대응표본 t-검정
: 동일한 사람 또는 물건에 대한 측정 값이 두 개인 경우에 사용하는 분석방법이다. 
시간 상 전후의 개념이기 때문에 독립된 두 집단일 필요가 없다.

대응표본 t-검정을 진행할 실제 데이터를 찾지 못해 임의로 데이터를 만들고 진행해보겠다.

어떤 사람이 두 번 사격을 하여 다음과 같은 점수를 얻었다고 하자.


```python
pratice = [8, 9, 7, 6, 7, 8, 6, 8, 7, 9]
exam = [10, 9, 7, 8, 9, 10, 10, 8, 8, 9]

print("pratice의 p-value:", shapiro(pratice)[1], "\nexam의 p-value:", shapiro(exam)[1])
```

    pratice의 p-value: 0.2582412362098694 
    exam의 p-value: 0.1909903883934021
    

두 번 모두 p-value가 0.05 이상이므로 정규성을 만족한다.

<br>

다음으로 등분산성을 검정한다.


```python
print("p-value:", levene(pratice, exam)[1])
```

    p-value: 0.7030766072336114
    

p-value가 0.05보다 크므로 등분산성을 만족한다.

<br>

- 귀무가설 : 연습을 하기 전 점수와 후의 점수는 차이가 없다.
- 대립가설 : 연습을 하기 전 점수와 후의 점수는 차이가 있다.


```python
from scipy.stats import ttest_rel

print("p-value:", ttest_rel(pratice, exam)[1])
```

    p-value: 0.013275877464573012
    

p-value가 0.05보다 작으므로 대립가설이 채택된다.

즉, 연습을 하기 전과 후의 점수는 차이가 있다라고 할 수 있다.

<br><br>

### Mann-Whitney U test
: 두 집단의 데이터가 정규성을 만족하지 않거나 집단의 데이터가 작을 때 두 집단의 차이를 분석하는 방법이다.
두 집단 각각의 값들의 순위들을 합한 것을 사용하여 진행한다.

예를 들어 A학과와 B학과의 점수를 예로 들어 Mann-Whitney U test를 해보겠다.

- 귀무가설 : A학과와 B학과의 등수의 차이가 없다.
- 대립가설 : A학과와 B학과의 등수의 차이가 있다.


```python
from scipy.stats import mannwhitneyu

A = [80, 70, 65, 90, 95]
B = [100, 95, 65, 75, 75]

print("p-value:", mannwhitneyu(A, B)[1])
```

    p-value: 0.4165144468597607
    

p-value가 0.05 이상이므로 귀무가설이 채택된다.

즉, A학과와 B학과의 등수에는 차이가 없다라고 할 수 있다.

<br>

**Mann-Whitney U test는 순위만 비교한 것이기 때문에 두 집단의 크기의 차이를 언급할 수 없다는 단점이 있지만, 
정규분포에 대한 가정을 하지 않기 때문에 순서가 있는 경우에는 어떠한 경우에도 사용할 수 있다는 장점이 있다.**

