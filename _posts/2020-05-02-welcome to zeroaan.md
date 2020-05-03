---
layout: post
title:  "Python List 값 제거하기"
date:   2020-05-02 19:43:59
author: zeroaan
categories: python
# tags: python code
# cover:  "/assets/header_image.jpg"
---

# 리스트 값 제거

#### remove 함수 사용

```python
list = ['kim', 'lee', 'park', 'choi']

list.remove('park') # 'park' 삭제

print(list)
```
`['kim', 'lee', 'choi']`

**리스트에 같은 값이 있을 경우에는 앞에 있는 값이 사라진다.*

<br><br>

#### 만약 리스트에 있는 해당 값을 모두 지우고 싶다면 반복문을 사용해 지워야 한다.

```python
list2 = ['kim', 'lee', 'park', 'choi', 'lee', 'lee']

while 'lee' in list2:
    list2.remove('lee') # 'lee' 삭제

print(list2)
```
`['kim', 'park', 'choi']`