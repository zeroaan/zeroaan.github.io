---
layout: post
title:  "[Python] 리스트 ↔ 문자열 변환하기(split, join)"
date:   2020-05-12 17:07:32
author: zeroaan
categories: python
# tags: python code
# cover:  "/assets/header_image.jpg"
---

파이썬에서는 리스트를 문자열로, 문자열을 리스트로 합치고 나누면서 변환이 가능하다.

<br>

먼저 문자열을 리스트로 만들기 위해서는 split 함수를 사용한다.<br>
사용법 : `문자열.split(구분)`

<br>

리스트를 문자열로 만들기 위해 join 함수를 사용한다.<br>
사용법 : `"".join(리스트)`

<br>

#### 1. 문자열 → 리스트 변환
```python
address = "172.665.123.62"

list_address = address.split(".") # "." 을 기준으로 하여 리스트로 변환한다

print(list_address)
```
`['172', '665', '123', '62']`

<br>

#### 2. 리스트 → 문자열 변환
```python
number = ['A', 'B', 'C', 'D', 'E', 'F']

str_number = "".join(number)

print(str_number)
```
`ABCDEF`

<br>

위와 같은 방법은 문자열로 단순히 붙이기만 하기 때문에 문자 사이에 특정한 문자를 넣고 싶다면 "" 사이에 특정 문자를 넣어주면 된다.
```python
animal = ['하마', '원숭이', '사자', '호랑이', '고양이', '강아지']

str_animal = "-".join(animal) # ", " 를 포함하여 문자열로 변환한다

print(str_animal)
```
`하마-원숭이-사자-호랑이-고양이-강아지`