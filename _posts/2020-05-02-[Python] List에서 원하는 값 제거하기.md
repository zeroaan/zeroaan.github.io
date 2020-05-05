---
layout: post
title:  "[Python] List에서 원하는 값 제거하기"
date:   2020-05-02 19:43:59
author: zeroaan
categories: python
# tags: python code
# cover:  "/assets/header_image.jpg"
---

### list 에서 원하는 값을 제거하고 싶을 때 사용할 수 있는 함수는 remove, pop, clear 그리고 del 키워드가 있다.

- remove 함수를 사용해 자신이 지우고 싶은 값을 제거할 수 있다.
- del키워드와 pop 함수는 해당 인덱스 값을 이용해 값을 제거할 수 있다.
- clear 함수는 리스트 원소의 값을 모두 삭제한다.

<br>

#### remove 함수 사용

```python
list = ['kim', 'lee', 'park', 'choi']

list.remove('park') # 'park' 삭제

print(list)
```
`['kim', 'lee', 'choi']`

**리스트에 같은 값이 있을 경우에는 앞에 있는 값이 사라진다.*

<br>

#### 만약 리스트에 있는 해당 값을 모두 지우고 싶다면 반복문을 사용해 지워야 한다.

```python
list2 = ['kim', 'lee', 'park', 'choi', 'lee', 'lee']

while 'lee' in list2:
    list2.remove('lee') # 'lee' 삭제

print(list2)
```
`['kim', 'park', 'choi']`

<br>

#### del 키워드 사용

```python
list3 = ['zero', 'one', 'two', 'three']

del list3[2] # 두 번째 인덱스 값 삭제

print(list3)
```
`['zero', 'one', 'three']`

```python
list4 = [0, 1, 2, 3, 4, 5]

del list4[2:5] # 두 번째 인덱스부터 네 번째 인덱스 까지 삭제

print(list4)
```
`[0, 1, 5]`

<br>

#### pop 함수 사용

```python
list5 = ['what', 'why', 'where', 'how', 'when']

list5.pop(1) # 첫 번째 인덱스 값('why') 삭제

print(list5)
```
`['what', 'where', 'how', 'when']`

<br>

#### clear 함수 사용

```python
list6 = ['a', 'b', 'c', 'd', 'e']

list6.clear() # 리스트 원소 모두 삭제

print(list6)
```

`[]`