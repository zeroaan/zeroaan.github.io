---
layout: post
title:  "[ML] Logistic Regression(로지스틱 회귀분석)"
date:   2020-06-02 21:03:25
author: zeroaan
categories: ml/dl
use_math: true
# tags: python code
# cover:  "/assets/header_image.jpg"
---

Logistic Regression(로지스틱 회귀)는 데이터가 어떤 범주에 속할 확률을 0에서 1 사이의 값으로 예측하고 그 확률에 따라 가능성이 더 높은 범주에 속하는 것으로 분류해주는 알고리즘이다.

![logistic_curve]({{site.baseurl}}/img/logistic_curve.png)

종속변수가 연속형인 선형회귀(Linear Regression)와 다르게 Logistic Regression은 종속변수가 범주형이거나 0과 1 인 경우에 사용한다.

<br>

Logistic Regression 에서는 y의 값이 확률이기 때문에 0과 1 사이의 값이 나오게 된다.

이 식에서 x값은 -∞ ~ +∞ 사이의 값을 가지게 되지만 y값은 확률이기 때문에 0 ~ 1의 값을 갖게 된다.

`y = ax + b`

그렇기 때문에 y값이 다시 -∞ ~ +∞ 사이의 값을 갖을 수 있게 수식을 변환시켜줘야 하는데 이 때 Odds 라는 개념이 사용된다.

<br>

#### Odds는 어떤 일이 일어날 확률(1이 될 확률 P)을 일어나지 않을 확률(1-P)로 나눈 것을 말한다.
<br>
### $ Odds = \frac {P} {1-P} $

이렇게 하게 되면 확률(P)가 1에 가까워 질수록 Odds는 +∞ 에 가까워지고 확률이 0에 가까워 질수록 Odds는 0에 가까워진다.

<br>

하지만 아직 0 ~ +∞ 사이의 값이므로 Odds 값에 log를 씌워서 만들어준다.

### $ log(Odds) = log(\frac {P} {1-P}) $ 

이렇게 된다면 log(Odds) 값은 -∞ ~ +∞ 사이의 값을 가지게 된다.

<br><br>

#### ① 다시 돌아가 P에 관하여 식을 정리해보면

### $ log(\frac {P} {1-P}) = ax + b $

<br><br>

#### ② 양변에 e를 씌워준다.

### $ \frac {P} {1-P} =  e^{ax+b} $ 

<br><br>

#### ③ 그리고 역수를 취한다.

### $ \frac {1-P} {P} = \frac {1} {e^{ax+b}} $

### $ \frac {1} {P} - 1 = \frac {1} {e^{ax+b}} $

### $ \frac {1} {P} = \frac {1} {e^{ax+b}} + 1 $

### $ \frac {1} {P} = \frac {1 + e^{ax+b}} {e^{ax+b}} $

<br><br>

#### ④ 다시 역수를 취한다.

### $ P = \frac {e^{ax+b}} {1 + e^{ax+b}}  $

<br><br>

이 식을 그래프로 그려보면 아래와 같은 곡선이 나오는데 이 곡선을 Logistic Curve 라 부른다.

![logistic_curve]({{site.baseurl}}/img/logistic_curve.png)