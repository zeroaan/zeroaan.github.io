---
layout: post
title:  "[Git] github 사용법과 기초 명령어"
date:   2020-05-10 16:14:05
author: zeroaan
categories: git
# tags: python code
# cover:  "/assets/header_image.jpg"
---

Github는 개발자들을 위한 소스코드 관리 서비스이다. 
소스 코드를 업로드할 수 있고 공동 협업을 통해 코드 공유 및 수정이 가능하다.

#### 저장소
먼저 저장소에 대해서 알아보겠다. 저장소는 디렉터리나 파일들을 저장하는 곳이다. 저장소에는 로컬 저장소와 원격 저장소가 있으며 **로컬 저장소**는 자신의 컴퓨터에 있는 저장소를 말하고 **원격 저장소**는 github 네트워크 상에 있는 저장소를 말한다. 일반적으로는 로컬 저장소에서 파일 생성 및 편집을 하고 그 후에 원격 저장소에 저장하게 된다.

#### 기본적인 github 명령어
기초적인 github 사용법은 아래와 같다.
- github 저장소 생성(git init)
- 파일 생성 및 편집
- 파일의 변경 사항을 git 인덱스에 추가(git add)
- 그 후 변경 사항을 확정하고 로컬 저장소에 로그 생성(git commit)
- 로컬 저장소와 원격 저장소를 연결(git remote)
- 로컬 저장소에 변경 사항을 원격 저장소에 저장(git push)

<br>

#### 1. github 저장소 생성
github에서 **Create a new repository**를 클릭한다.

**Repository name**을 입력하고 선택사항으로 Description을 입력해준다. 저장소 유형으로는 **Public**으로 선택한다. 저장소에 미리 README 파일을 만들어 놓을 경우에는 **Initialize this repository with a README**를 체크해주고 아닐 경우에는 체크 해제한다. 선택이 완료되면 **Create repository** 버튼을 클릭하여 저장소를 생성한다.
![create](./img/create.png)

<br>

#### 2. 자신의 컴퓨터에 저장소 생성
명령어 : `git init`

cmd 창에서 로컬 저장소로 사용할 디렉터리로 이동 후 **git init** 명령을 통해 현재 디렉터리를 git 저장소로 사용한다. 이 명령을 실행하면 해당 디렉터리에 .git 이라는 하위 디렉터리가 생성된다.
![init](./img/init.png)

<br>

#### 3. 파일 생성 및 편집 후 인덱스 추가
명령어 : `git add [파일명]`

로컬 저장소에 파일을 1개 생성하고 **git add [파일명]** 명령을 통해 저장소에 커밋 할 준비를 한다. 이 명령을 실행하면 해당 파일은 staging area로 이동하게 된다. 즉, 커밋을 위한 대기영역으로 가게 된다.
![add](./img/add.png)

<br>

#### 4. 변경 사항을 확정하고 로그 생성
명령어 : `git commit -m [커밋 메시지]

git add 명령 후에 추가 변동사항이 없으면 **git commit -m [커밋 메시지]** 명령을 통해 파일이나 디렉터리의 변경 사항을 저장소에 기록한다. 이 명령을 실행하면 입력한 [커밋 메시지]가 로그로 등록된다.
![commit](./img/commit.png)

<br>

#### 5. 로컬 저장소와 원격 저장소 연결
명령어 : `git remote add [별명] [원격저장소 주소]`

원격 저장소에 반영하기 전에 로컬 저장소와 원격 저장소를 연결해준다. 처음 연결할 때의 [별명]은 일반적으로 **origin** 으로 설정하고 [원격저장소 주소]는 아까 만든 repository 주소를 입력한다.
![remote](./img/remote.png)

<br>

#### 6. 로컬 저장소의 변경 사항을 원격 저장소에 저장 
명령어 : `git push [별명] [브랜치명]`

처음 원격 저장소를 만들면 **master** 브랜치가 만들어진다. 별명은 아까 remote 할 때 설정해준 별명을 입력해준다. 일반적으로 **git push origin master** 를 입력한다. 이 명령을 실행하면 github 저장소에 변경 사항이 반영된다. 
![push](./img/push.png)

<br>

#### 추가적으로 **git status** 명령을 통해 현재 디렉터리의 상태와 변경사항을 확인할 수 있다.
명령어 : `git status`

git add 명령을 통해 변경 사항 인덱스를 추가해주고 commit 해주기 전 상태이다.
![status](./img/status.png)