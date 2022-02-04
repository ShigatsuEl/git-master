# Undo

## Local Changes

### Unstaging a staged file

```
git reset HEAD file.txt -> 깃이 HEAD시점에 있는 file.txt 파일을 초기화시킨다.
```

### Unmodifying a modified file

```
git checkout -- file.txt -> 이미 Modifyied 된 파일을 초기화합니다.
```

### Discarding local changes

```
git restore --staged file.txt #Staging된 파일을 Unstaged 상태로 초기화합니다.
git restore file.txt #Wokring directory에서 Modifying된 파일을 초기화합니다.
git restore . #Working directory에서 Modifying된 모든 파일들을 초기화합니다.
git clean -fd #Untracked된 파일들을 삭제합니다.
```

## Restoring file from certain commit

```
git restore --source=hash file.txt -> 해쉬 커밋시점으로 file.txt파일을 초기화한다.
git restore --source=HEAD~2 file.txt -> HEAD에서 2번째 떨어진 커밋시점으로 file.txt파일을 초기화한다.
```

## Commit

### Amending the last commit

```
git commit --amend -> 마지막 커밋을 고칠 수 있습니다.
// 예를 들어 마지막 커밋을 수정하고 싶으면 working directory에서 수정 후 git add로 추가해주고 git commit --amend를 사용하면 마지막 커밋에 다시 적용하게 된다.
git commit --amend -m -> 마지막 커밋의 메시지를 수정할 수 있습니다.
```

## Reset

```
git reset --soft HEAD #커밋을 삭제하면서 staging area에 커밋코드를 남겨놓습니다.
git reset --mixed HEAD #커밋을 삭제하면서 working directory에 커밋코드를 남겨놓습니다.
git reset --hard HEAD #커밋을 삭제하고 커밋내역마저 삭제합니다.(working drectory or staging area 둘 다 남겨놓지 않음)
```

## Undo action - reflog

커밋을 하다 실수해서 예전으로 돌아가고 싶다면? reflog를 사용한다.<br>
한가지 명심해야 할 점은 reflog를 사용할 때는 로컬 저장소에서만 사용해야 한다는 것이다.<br>
원격 저장소에 커밋이 이미 푸쉬된 경우, 컨플릭트가 발생할 수 있으며 혼란이 오기 때문에 사용하지 않는다.<br>

```
git reflog -> reflog 명령어를 사용해 우리가 해왔던 커밋 중 원하는 시점으로 돌아갈 수 있다. 매우 갓갓이긴 로컬 저장소에서만 사용하는 것이 좋다.
git reset --hard hash -> reflog에서 돌아가길 원하는 커밋의 해시코드를 reset --hard하면 그 커밋의 시점으로 돌아갈 수 있다. 다만, 커밋이 되지 않은 상황에서 사용하면 작업하고 있던 내용들이 다 날라가버리니 주의해야 한다.
```

## Revert

이미 원격 저장소에 푸쉬했지만 커밋을 취소하고 싶은 경우 `revert`를 사용한다.<br>

```
git revert hash #해쉬 커밋을 취소한다.
git revert HEAD~1 #HEAD에서 첫번째 떨어진 커밋을 취소한다.
gut revert --no-commit hash #해쉬 커밋을 취소하는데 커밋을 남기지 않고 변경사항을 Staging area로 가져온다. 다만, Staging area에 있는 내용을 수정하는 것은 안되고(충돌이 발생함) 이미 충돌이 발생하는 경우에 수동으로 수정해야할 경우에만 사용한다.
```

## Interactive Rebasing

```
git rebase -i HEAD~2 -> commit --amend는 마지막 커밋만 수정이 가능했지만 rebase -i는 모든 커밋에 대해 수정이 가능하다. 이것 역시 로컬 저장소에서만 사용하도록 한다.
git rebase --continue
git rebase --abort
```

[(C)Dream Coding Academy](https://academy.dream-coding.com/)
