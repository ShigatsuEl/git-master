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
