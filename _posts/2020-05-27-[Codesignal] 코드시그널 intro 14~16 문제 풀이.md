---
layout: post
title:  "[Codesignal] 코드시그널 intro 14~16 문제 풀이"
date:   2020-05-27 15:54:02
author: zeroaan
categories: codesignal
# tags: python code
# cover:  "/assets/header_image.jpg"
---

#### 14. alternatingSums.py
: Several people are standing in a row and need to be divided into two teams. The first person goes into team 1, the second goes into team 2, the third goes into team 1 again, the fourth into team 2, and so on.

```python
def alternatingSums(a):
    team_1, team_2 = 0, 0
    
    for i in range(len(a)):
        if i % 2 == 0:
            team_1 += a[i]
        else: team_2 += a[i]

    return [team_1, team_2]
```
<a href="https://zeroaan.github.io/python/2020/05/18/Python-%EB%A6%AC%EC%8A%A4%ED%8A%B8-%EB%B0%B0%EC%97%B4-index-%EC%82%AC%EC%9A%A9%EB%B2%95.html" style="color: blue">배열 index 사용법</a> 를 알고나서 한 줄로 코드를 변경하였다.<br>
```python
def alternatingSums(a):
    return [sum(a[::2]), sum(a[1::2])]
```

<br>

#### 15. addBorder.py
:  Given a rectangular matrix of characters, add a border of asterisks(*) to it.

```python
def addBorder(picture):
    result = []
    col = len(picture[0]) + 2
    row = len(picture) + 2
    result.append('*' * col)

    for i in range(len(picture)):
        value = '*'
        for j in range(len(picture[i])):
            value  += picture[i][j]
        value += '*'
        result.append(value)

    result.append('*' * col)
    return result
```
위의 코드도 통과는 하였지만 이중 for문을 사용하였기 때문에 다음 코드로 변경하였다.<br>
```python
def addBorder(picture):
    result = []
    col = len(picture[0]) + 2
    result.append('*' * col)

    for i in picture:
        result.append('*' + i + '*')

    result.append('*' * col)
    return result
```

<br>

#### 16. areSimilar.py
:  Two arrays are called similar if one can be obtained from another by swapping at most one pair of elements in one of the arrays. Given two arrays a and b, check whether they are similar.

```python
def areSimilar(a, b):
    if a == b:
        return True

    value = []
    for i in range(len(a)):
        if a[i] != b[i]:
            value.append(i)

    a[value[0]], a[value[1]] = a[value[1]], a[value[0]]
    return a == b
```
위의 코드로도 문제는 통과는 된다. <br>
하지만 a와 b 에서 값 하나만 틀릴 경우 에러가 발생할 수 있기 때문에 코드를 수정해보았다.<br>
```python
def areSimilar(a, b):
    if a == b:
        return True

    value = []
    for i in range(len(a)):
        if a[i] != b[i]:
            value.append(i)
    
    # 13 ~ 14줄은 없어도 문제 통과는 되지만
    # 만약 a = [1, 2, 2], b = [2, 2, 2] 일 경우
    # 16줄에서 인덱스 에러가 나기 때문에 해당 줄을 추가해주었다.
    if len(value) != 2:
        return False

    a[value[0]], a[value[1]] = a[value[1]], a[value[0]]
    return a == b
```