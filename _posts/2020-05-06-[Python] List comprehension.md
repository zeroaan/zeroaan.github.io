---
layout: post
title:  "[Python] List comprehension"
date:   2020-05-06 20:42:19
author: zeroaan
categories: python
# tags: python code
# cover:  "/assets/header_image.jpg"
---

Python 에서 list comprehension 은 리스트를 짧게 한 줄로 만들 수 있는 방법이다.

일반적으로는 코드를 짤 때 빈 리스트를 생성하고 for문을 사용해 값을 리스트에 넣는 방법으로 진행하지만
list comprehension 방법을 이용하면 더 빠르고 쉽게 코드를 짤 수 있다.

<br>

#### 일반적인 방법

```python
arr = []

for i in range(10):
  arr.append(i*3)
print(arr)
```
`[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]`

<br>

#### list comprehension

```python
arr2 = [i*3 for i in range(10)]
print(arr2)
```
`[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]`

<br>

#### 추가적으로 조건문을 사용해 list comprehension이 가능하다.
```python
arr3 = [i*3 for i in range(10) if i % 2 == 0]
print(arr3)
```
`[0, 2, 4, 6, 8]`