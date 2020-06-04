---
layout: post
title:  "[ML] KNN 알고리즘(K-Nearest Neighbor)"
date:   2020-06-01 21:46:56
author: zeroaan
categories: ml/dl
use_math: true
# tags: python code
# cover:  "/assets/header_image.jpg"
---

### K-Nearest Neighbors 알고리즘
새로운 데이터 포인트에 대해 예측할 때 알고리즘이 훈련 데이터 셋에서 가장 가까운 데이터 포인트를 찾아 예측한다.

![knn_k1]({{site.baseurl}}/img/knn_k1.png)

K=1 일 때는 가장 가까운 데이터 하나만 찾아 가장 가까운 값으로 예측이 된다.

<br>

![knn_k3]({{site.baseurl}}/img/knn_k3.png)

K=3 일 때는 가까운 데이터 3개만 보기 때문에 3개의 값중 다수의 값으로 예측이 된다.

<br>

K의 값이 클 때보다 K의 값이 작을 수록 훈련 데이터에 가깝게 따라간다.

다시 말해서, K가 1에 가까울수록 모델이 복잡해지고 K를 점점 늘릴수록 모델이 단순 해진다는 것을 알 수 있다.

![knn_k1_3_9]({{site.baseurl}}/img/knn_k1_3_9.png)

그림을 보면 이웃을 하나 선택했을 때는 경계가 훈련 데이터에 가깝게 따라가고 있고, 이웃의 수를 늘릴수록 경계가 더 부드러우지는 것을 볼 수 있다.

즉, K가 작을수록 overfitting이 생길 수 있고, K가 클수록 underfitting이 생길 수 있다.

<br>

실제 데이터인 유방암 데이터 셋으로 KNN을 진행해보겠다.


```python
import mglearn
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.neighbors import KNeighborsClassifier
from sklearn.datasets import load_breast_cancer

cancer = load_breast_cancer()
X_train, X_test, y_train, y_test = train_test_split(cancer.data, cancer.target, stratify=cancer.target, random_state=66)

training_accuracy = []
test_accuracy = []

neighbors_settings = range(1, 11)

for n_neighbors in neighbors_settings:
    clf = KNeighborsClassifier(n_neighbors=n_neighbors)
    clf.fit(X_train, y_train)
    training_accuracy.append(clf.score(X_train, y_train))
    test_accuracy.append(clf.score(X_test, y_test))

plt.rc('font', family='Malgun Gothic')
plt.plot(neighbors_settings, training_accuracy, label="훈련 정확도")
plt.plot(neighbors_settings, test_accuracy, label="테스트 정확도")
plt.xlabel("n_neighbors")
plt.ylabel("정확도")
plt.legend()
```

![knn_graph]({{site.baseurl}}/img/knn_graph.png)


K=1 일 때는 훈련 데이터에 대해 예측이 완벽하지만 K의 값이 커질수록 모델은 단순해지고 정확도는 줄어든다. 테스트 세트는 반대로 K=1 인 정확도가 K가 클 때보다 낮다.

이것은 K의 값이 낮을 때 모델을 너무 복잡하게 만든다는 것을 알 수 있고, 반대로 K의 값이 클 때는 모델이 너무 단순해진다는 것을 알 수 있다.

정확도가 가장 좋을 때는 K=6 일 때로 너무 복잡하지도 간단하지도 않은 K의 값을 찾아야 한다.

<br>

#### K-NN의 장점
- 이해하기 매우 쉬운 모델
- 많이 조정할 필요가 없음

#### K-NN의 단점
- 훈련 세트가 클 경우 예측이 느려짐
- 많은 특성을 처리하는 능력이 부족
