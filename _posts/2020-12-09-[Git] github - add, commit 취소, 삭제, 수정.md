---
layout: post
title:  "[Git] github - add, commit 취소, 삭제, 수정"
date:   2020-12-09 11:14:50
author: zeroaan
categories: git
# tags: python code
# cover:  "/assets/header_image.jpg"
---

add와 commit 에 대해서 취소, 삭제, 수정하는 방법을 알아보겠다.

<br>

#### 관련명령어
- git reset HEAD [파일명] : add 취소
- git reset HEAD^ 또는 HEAD~3 : 가장 마지막 commit 취소 / 최근 3개 commit 취소
- git commit --amend : 가장 마지막 commit 수정
- git rebase -i HEAD~3 : 최근 3개 commit 수정
- git push -f origin main : 원격저장소에 반영

<br>

#### 1. git reset HEAD [파일명]
- 현재 staging 영역에 있는 add 된 파일들을 취소할 수 있다.
- git reset HEAD 로 뒤에 [파일명]을 붙이지 않으면 모든 add 가 취소된다.

<br>

#### 2. git reset HEAD^ 또는 HEAD~3
- git reset HEAD^는 가장 마지막 commit을 취소할 수 있다.
- git reset HEAD~3은 최근 3개의 commit을 취소할 수 있다.

<br>

#### 3. git commit --amend
- 가장 마지막 commit을 수정할 수 있다.

<br>

#### 4.git rebase -i HEAD~3
- 최근 3개의 commit을 수정할 수 있다.
- git log 명령을 통해 자신이 변경하고 싶은 commit이 몇 번째인지 확인 후 사용

<br>

#### 5. git push -f origin main
- 이미 commit이 원격저장소에 올라갔을 경우 사용한다.
- 위의 명령들을 통해 적용된 사항을 원격 저장소에 반영한다.