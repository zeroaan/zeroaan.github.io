---
layout: post
title:  "[Git] github 사용법과 기초 명령어"
date:   2020-05-10 16:14:05
author: zeroaan
categories: git
# tags: python code
# cover:  "/assets/header_image.jpg"
---

branch를 생성하여 github를 관리할 수 있다.

<br>

#### 브랜치(Branch) 관련 명령어
- git branch : 브랜치 리스트, 현재 브랜치 확인
- git branch [브랜치명] : 새로운 branch 생성
- git branch -m [브랜치명] : 브랜치 이름 변경
- git checkout [브랜치명] : 브랜치 이동
- git checkout -b [브랜치명] : 새로운 branch 생성 후 이동
- git branch -D [브랜치명] : 브랜치 삭제

<br>

#### 1. git branch
branch 리스트를 볼 수 있다.

![branch_1]({{site.baseurl}}/img/branch_1.png)

<br>

#### 2. git branch [브랜치명]
입력한 브랜치명으로 새로운 branch를 생성한다.

![branch_2]({{site.baseurl}}/img/branch_2.png)

<br>

#### 3. git branch -m [브랜치명]
입력한 브랜치명으로 branch 이름을 변경한다.<br>
>> 바꾸고자 하는 브랜치로 이동 후 변경해주어야 함.

![branch_3]({{site.baseurl}}/img/branch_3.png)

<br>

#### 4. git checkout [브랜치명]
입력한 브랜치로 이동한다.

![branch_4]({{site.baseurl}}/img/branch_4.png)

<br>

#### 5. git checkout -b [브랜치명]
입력한 브랜치명으로 새로운 branch를 생성 후 해당 브랜치로 이동한다.

![branch_5]({{site.baseurl}}/img/branch_5.png)

<br>

#### 6. git branch -D [브랜치명]
입력한 브랜치를 삭제한다.<br>

만약 git push를 통해 생성된 branch를 연결해주었다면 추가 명령을 입력해주어야 한다.<br>
이 때 local branch는 삭제 되었으나, remote branch는 삭제 되지 않아 다음 명령어도 입력해주어야 한다.<br>

git push origin :[브랜치명]

![branch_6]({{site.baseurl}}/img/branch_6.png)