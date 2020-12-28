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
![01-1](./01-1.PNG)

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
