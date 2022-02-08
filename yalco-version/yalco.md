# Yalco Version

## 시간 여행하기

### 프로젝트의 변경사항들을 타임캡슐(버전)에 담기

- 변경사항 확인

```
git status
```

- 파일 하나 담기

```
git add tigers.yaml
```

- 모든 파일 담기

```
git add .
```

### 타임캡슐 묻기

- 아래 명령어로 commit

```
git commit
```

- VI 입력 모드로 진입

|        작업         | Vi 명령어 |                     상세                     |
| :-----------------: | :-------: | :------------------------------------------: |
|      입력 시작      |     i     | 명령어 입력 모드에서 텍스트 입력 모드로 전환 |
|      입력 종료      |    ESC    | 텍스트 입력 모드에서 명령어 입력 모드로 전환 |
|   저장 없이 종료    |    :q     |                                              |
| 저장 없이 강제 종료 |    :q!    |           입력한 것이 있을 때 사용           |
|    저장하고 종료    |    :wq    |           입력한 것이 있을 때 사용           |
|     위로 스크롤     |     k     |       git log등에서 내역이 길 때 사용        |
|    아래로 스크롤    |     j     |       git log등에서 내역이 길 때 사용        |

- 커밋 메시지와 함께 작성하기

```
git commit -m "FIRST COMMIT"
```

- 아래 명령어와 소스트리로 확인

```
git log
```

### 과거로 돌아가는 두 가지 방법

Git에서 과거로 돌아가는 두 방식

- reset : 원하는 시점으로 돌아간 뒤 이후 내역들을 지웁니다.
- revert : 되돌리기 원하는 시점의 커밋을 거꾸로 실행합니다.

#### reset 사용해서 과거로 돌아가기

```
git reset --hard (돌아갈 커밋 해시)
```

#### reset 하기 전 시점으로 복원해보기

```
git reset --hard
```

#### revert 로 과거의 커밋 되돌리기

```
git revert (되돌릴 커밋 해시)
git revert --no-commit (되돌릴  커밋 해시)
```

## 차원 넘나들기

### 여러 branch 만들어보기

#### 브랜치 생성 / 이동 / 삭제하기

- add-coach란 이름의 브랜치 생성

```
git branch add-coach
```

- 브랜치 목록 확인

```
git branch
```

- add-coach 브랜치로 이동

```
git switch add-coach
```

- 브랜치 생성과 동시에 이동하기

```
git switch -c new-teams
```

- 브랜치 삭제하기

```
git branch -d (삭제할 브랜치명)
git branch -D (강제삭제할 브랜치명) // 강제삭제
```

- 브랜치 이름 바꾸기

```
git branch -m (기존 브랜치명) (새 브랜치명)
```

### branch를 합치는 두 가지 방법

- merge : 두 브랜치를 한 커밋에 이어붙입니다.

  브랜치 사용내역을 남길 필요가 있을 때 적합한 방식입니다.
  다른 형태의 merge에 대해서도 이후 다루게 될 것입니다.

- rebase : 브랜치를 다른 브랜치에 이어붙입니다.

  한 줄로 깔끔히 정리된 내역을 유지하기 원할 때 적합합니다.
  이미 팀원과 공유된 커밋들에 대해서는 사용하지 않는 것이 좋습니다.

### branch 합치기 실습

#### merge로 합치기

add-coach 브랜치를 main 브랜치로 merge

1. main 브랜치로 이동
2. 아래의 명령어로 병합

```
git merge add-coach
```

merge는 reset으로 되돌리기 가능

- merge도 하나의 커밋
- merge하기 전 해당 브랜치의 마지막 시점으로

병합된 브랜치는 삭제

```
git branch -d add-coach
```

#### rebase로 합치기

new-teams 브랜치를 main 브랜치로 rebase

1. new-teams 브랜치로 이동
2. merge때와는 반대!
3. 아래의 명령어로 병합

```
git rebase main
```

4. main 브랜치로 이동 후 아래 명령어로 new-teams의 시점으로 fast-forward

```
git merge new-teams
```

5. new-teams 브랜치 삭제

### 충돌 해결하기

#### merge 충돌 해결하기

당장 충돌 해결이 어려울 경우 아래 명령어로 merge 중단

```
git merge --abort
```

해결 가능 시 충돌 부분을 수정한 뒤 git add ., git commit으로 병합 완료

#### rebase 충돌 해결하기

당장 충돌 해결이 어려울 경우 아래 명령어로 merge 중단

```
git rebase --abort
```

해결 가능 시
충돌 부분을 수정한 뒤 git add .
아래 명령어로 계속

```
git rebase --continue
```

충돌이 모두 해결될 때까지 반복

## GitHub 사용하기

### 원격 저장소 사용하기

#### 로컬의 Git 저장소에 원격 저장소로의 연결 추가

원격 저장소 이름에 흔히 origin 사용. 다른 것으로 수정 가능

```
git remote add origin (원격 저장소 주소)
```

#### GitHub 권장 - 기본 브랜치명을 main으로

```
git branch -M main
```

#### 로컬 저장소의 커밋 내역들 원격으로 push(업로드)

-u 또는 --set-upstream : 현재 브랜치와 명시된 원격 브랜치 기본 연결

```
git branch -M main
```

### push와 pull

#### 원격으로 커밋 밀어올리기(push)

```
git push
```

이미 git push -u origin main으로 대상 원격 브랜치가 지정되었기 때문에 가능

#### 원격의 커밋 당겨오기(pull)

```
git pull
```

#### pull 할 것이 있을 때 push를 하면?

1. 로컬에서 내용 수정

2. GitHub에서 수정(다른 사람이 먼저 push를 했다고 가정) 후 push

3. push 해보기

원격에 먼저 적용된 새 버전이 있으므로 적용 불가
pull 해서 원격의 버전을 받아온 다음 push 가능

4. push 할 것이 있을 시 pull 하는 두 가지 방법

- `git pull --no-rebase` - merge 방식

- `git pull --rebase` - rebase 방식

  pull 상의 rebase는 다름 (협업시 사용 OK)

5. push하기

#### 협업상 충돌 발생 해결하기

1. 로컬에서 파일 내용 수정

2. 원격에서 같은 파일의 같은 내용 수정(다른 사람이 먼저 push를 했다고 가정) 후 push

3. pull 하여 충돌상황 마주하기

#### 로컬의 내역 강제 push해보기

로컬의 내역 충돌 전으로 reset

```
git push --force
```

### 원격의 브랜치 다루기

#### 로컬에서 브랜치 만들어 원격에 push 해보기

1. from-local 브랜치 만들기

2. 아래 명령어로 원격에 push

```
git push -u origin from-local
git push(1번 라인 이후)
```

3. 브랜치 목록 살펴보기

```
git branch --all
```

#### 원격의 브랜치 로컬에 받아오기

1. GitHub에서 from-remote 브랜치 만들기

2. 아래 명령어로 원격의 변경사항 확인

```
git fetch
git branch -a
```

3. 아래 명령어로 로컬에 같은 이름의 브랜치를 생성하여 연결하고 switch

```
git switch -t origin/from-remote
```

#### 원격의 브랜치 삭제

```
git push (원격 이름) --delete (원격의 브랜치명)
```

## Git 보다 깊이 알기

### Git의 3가지 공간

- Working directory

  untracked: Add된 적 없는 파일, ignore 된 파일

  tracked: Add된 적 있고 변경내역이 있는 파일

  git add 명령어로 Staging area로 이동

- Staging area

  커밋을 위한 준비 단계

  git commit 명령어로 repository로 이동

- Repository

  .git directory라고도 불림

  커밋된 상태

#### 파일의 삭제와 이동

```
git rm
```

```
git mv
```

#### 파일을 staging area에서 working directory로

```
git restore --staged (파일명)
git restore (파일명) --staged를 빼면 working directory에서도 제거
```

#### reset의 세 가지 옵션

- --soft: repository에서 staging area로 이동
- --mixed (default): repository에서 working directory로 이동
- --hard: 수정사항 완전히 삭제

### HEAD

#### checkout으로 앞뒤 이동해보기

^ 또는 ~: 갯수만큼 이전으로 이동

```
git checkout HEAD^
git checkout HEAD~5
```

#### HEAD 사용하여 reset하기

```
git reset HEAD(원하는 단계) (옵션)
```

### fetch vs. pull

#### fetch와 pull의 차이

- fetch: 원격 저장소의 최신 커밋을 로컬로 가져오기만 함
- pull: 원격 저장소의 최신 커밋을 로컬로 가져와 merge 또는 rebase

#### 원격의 새 브랜치 확인

```
git checkout origin/(브랜치명)
git switch -t origin/(브랜치명)
```

## 프로답게 커밋 관리하기

### 어떻게 커밋하는게 좋을까요?

#### 작업을 커밋할 때 권장사항

1. 하나의 커밋에는 한 단위의 작업을 넣도록 합니다.

- 한 작업을 여러 버전에 걸쳐 커밋하지 않습니다.
- 여러 작업을 한 버전에 커밋하지 않습니다.

2. 커밋 메시지는 어떤 작업이 이뤄졌는지 알아볼 수 있도록 작성합니다.

#### 커밋 메시지 컨벤션

```
type: subject

body (optional)
...
...
...

footer (optional)
```

예시

```
feat: 압축파일 미리보기 기능 추가

사용자의 편의를 위해 압축을 풀기 전에
다음과 같이 압축파일 미리보기를 할 수 있도록 함
 - 마우스 오른쪽 클릭
 - 윈도우 탐색기 또는 맥 파인더의 미리보기 창

Closes #125
```

|   타입   |                      설명                       |
| :------: | :---------------------------------------------: |
|   feat   |                새로운 기능 추가                 |
|   fix    |                    버그 수정                    |
|   docs   |                    문서 수정                    |
|  style   |          공백, 세미콜론 등 스타일 수정          |
| refactor |                  코드 리팩토링                  |
|   perf   |                    성능 개선                    |
|   test   |                   테스트 추가                   |
|  chore   | 빌드 과정 또는 보조 기능(문서 생성기능 등) 수정 |

### 보다 세심하게 스테이징하고 커밋하기

#### 내용 확인하며 hunk별로 스테이징하기

```
git add -p
```

- 옵션 설명을 보려면 ?입력 후 엔터
- y 또는 n로 각 헝크 선택
- 일부만 스테이징하고 진행해보기
- git stats와 소스트리로 확인

#### 변경사항을 확인하고 커밋하기

```
git commit -v
```

j, k로 스크롤하며 내용 확인

### 커밋하기 애매한 변화 치워두기

#### 아래 명령어로 치워두기

```
git stash
```

#### 원하는 시점, 브랜치에서 다시 적용

```
git stash pop
```

#### 원하는 것만 stash 해보기

```
git stash -p
```

#### 스태시 목록 보기

```
git stash list
```

|             명령어             |                     설명                      |              비고              |
| :----------------------------: | :-------------------------------------------: | :----------------------------: |
|           git stash            |              현 작업들 치워두기               |         끝에 save 생략         |
|        git stash apply         |     치워둔 마지막 항목(번호 없을 시) 적용     |   끝에 번호로 항목 지정 가능   |
|         git stash drop         |     치워둔 마지막 항목(번호 없을 시) 삭제     |   끝에 번호로 항목 지정 가능   |
|         git stash pop          | 치워둔 마지막 항목(번호 없을 시) 적용 및 삭제 |          apply + drop          |
| 💡 git stash branch (브랜치명) |           새 브랜치를 생성하여 pop            | 충돌사항이 있는 상황 등에 유용 |
|        git stash clear         |           치워둔 모든 항목들 비우기           |                                |

### 과거의 커밋들을 수정, 삭제, 병합, 분할하기

git rebase -i (대상 바로 이전 커밋)

|  명령어   |        설명        |
| :-------: | :----------------: |
|  p, pick  |  커밋 그대로 두기  |
| r, reword |  커밋 메시지 변경  |
|  e, edit  |  수정을 위해 정지  |
|  d, drop  |     커밋 삭제      |
| s, squash | 이전 커밋에 합치기 |

## 취소와 되돌리기 보다 깊이 알기

### 관리되지 않는 파일들 삭제하기

`git clean`

| 옵션 |                 설명                 |
| :--: | :----------------------------------: |
|  -n  |        삭제될 파일들 보여주기        |
|  -i  |         인터렉티브 모드 시작         |
|  -d  |              폴더 포함               |
|  -f  |        강제로 바로 지워버리기        |
|  -x  | ⚠️ .gitignore에 등록된 파일들도 삭제 |

### 커밋하지 않은 변경사항 되돌리기

`git restore`

#### 파일 여러 개를 수정하고 아래 명령어들 사용해보기

```
git restore (파일명)
```

#### 변경상태를 스테이지에서 워킹 디렉토리로 돌려놓기

```
git restore --staged (파일명)
```

#### 파일을 특정 커밋의 상태로 되돌리기

```
git restore --source=(헤드 또는 커밋 해시) 파일명
```

### reset했어도 희망은 있다!

reflog 명령어

```
git reflog
```

reflog는 프로젝트가 위치한 커밋이 바뀔 때마다 기록되는 내역을 보여주고
이를 사용하여 reset하기 이전 시점으로 프로젝트를 복구할 수 있습니다.
