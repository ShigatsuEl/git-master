# Set Up

## Git Config

### See all the config

```
git config --list #깃 설정에 관한 모든 세팅을 보기
```

### Open config to edit

```
git config --global -e #깃 설정편집 파일을 오픈합니다.(global로 해야 전역으로 깃 설정이 된다.)

or

git config --global core.editor "code --wait" # 기본적으로 VSC로 깃 설정편집 파일을 오픈할 때까지 기다립니다.
```

### User Settings

```
git config --global user.name "name" #유저 이름을 전역으로 설정
git config --global user.email "email" #유저 이메일을 전역으로 설정
git config user.name #유저 이름을 확인
git config user.email #유저 이메일을 확인
```

### Set Auto CRLF

윈도우와 맥은 에디터에서 차이점이 있는데 바로 줄바꿈을 할 때,<br>
윈도우는 \r(carriage return)과 \n(line feed)가 동시에 있는 반면에<br>
맥은 \n(line feed)하나만 들어가게 된다.<br>
이러한 차이점 때문에 다양한 운영체제에서 Git Repository를 사용하는 경우에 내가 수정하지 않았음에도 불구하고 맥과 윈도우에서 발생하는 차이점 때문에 Git history가 달라져 협업을 하는데 문제가 발생할 수 있습니다.<br>
바로 이러한 차이점을 서로 맞추기 위해 생긴 것이 `core.autocrlf`입니다.
윈도우에서 `core.autocrlf = true`로 설정하게 되면 git에 저장할 때 \r(carriage return)을 삭제하게 되고 다시 깃에서 윈도우로 받아올 때는 \r(carriage return)을 붙혀서 가져오게 됩니다.<br>
반대로 맥에서는 `core,autocrlf = input`로 설정하게 되면 git에서 받아올 때는 별다른 수정을 하지 않으나 저장할 때는 \r(carriage return)을 삭제해 줍니다.<br>
맥에서 carriage return이 들어가지 않음에도 삭제해주는 이유는 실수로 carriage return이 들어갈 수 있기 때문에 방지해주는 역할을 하는 것 입니다.(아래 사진 참고)<br>
![01-1](01-1.png)

```
git config --global core.autocrlf true #윈도우 전용
git config --global core.autocrlf input #맥 전용
```

### Git Aliases

git에서 많이 사용하는 명령어를 Alias를 사용해 shortcut으로 재정의 할 수 있습니다.<br>

```
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
```

## Help

깃 명령어에 관한 도움말이 보고 싶다면 -> [Git Help](https://git-scm.com/docs)

```
git config --help #깃 설정에 관한 명령어를 자세히 보고 싶다면?
git config --h #위 help의 shortcut
```

## Git 초기화하고 Github에 push하기

먼저 Github에 push하기 위해서는 Git WorkFlow 흐름에 대해서 정확히 알고 있어야 한다.<br>
![01-2](01-2.png)
Git WorkFlow는 총 3가지 작업환경으로 나누어져 있습니다.<br>

1. 우리가 프로젝트의 파일을 수정하고 작업하고 있는 `working directory`가 있고<br>
2. 어느정도 작업하다가 버전 히스토리에 저장할 준비가 되어있는 파일들을 옮겨 놓는 `staging area`와
3. 버전의 히스토리를 가지고 있는 `git directory` or `git repository`로 나누어져 있습니다.<br>

즉, 우리는 VSC에서 아무것도 변경되지 않고 가지고 있는 `working directory`와 파일이 변경되면 변경된 내용을 기억하는 `staging area`, 그리고 변경된 내용을 업데이트 하는 `git directory` 총 3가지 환경으로 이루어져 있는 것 입니다.<br>

이러한 단계를 거쳐 우리는 Git의 변경내용을 Github에 히스토리(버전)별로 저장할 수 있습니다.<br>

1. git init(깃 저장소 생성)
2. git add .(working directory에서 변경된 내용을 staging area로 옮기는 과정) / git add .(현재 디렉토리에서 변경된 내용을 staging area로 옮김) or git add -p(working directory에서 변경된 파일들을 전부 보여주고 해당 파일을 하나하나 staging area로 옮길 것인지, 안 옮길 것인지 선택할 수 있다.) + `git status`는 working directory와 staging area의 상태를 확인하기 위해서 git add와 같이 자주 사용됩니다.<br>
3. git commit -m -> staging area에 있는 변경된 내용들 중 git repository에 저장할 내용만 commit하여 히스토리를 갱신할 수 있습니다.<br>
4. git remote add origin <url>(원격 저장소, 즉 깃허브 어디에 저장할 것인지를 정함)<br>
5. git push origin master(원격 저장소에 커밋을 푸쉬함 or 히스토리를 업데이트함!)<br>
