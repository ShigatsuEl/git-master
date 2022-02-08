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
