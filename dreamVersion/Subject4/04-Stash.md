# Stashing

## Saving

```
git stash push -m "message" #새로운 stash를 메시지와 함께 저장하게 됩니다.
git stash #아무 옵션 없이 stash 명령어만 사용하면 위와 같이 default 옵션인 push와 함께 저장하게 됩니다.
git stash --keep-index #--keep-index 옵션을 사용하면 작업하고 있는 내용들을 staging area에 남겨둠과 동시에 stash를 할 수 있습니다.
git stash -u #-u옵션을 사용하면 untracked된 파일들도 stash할 수 있습니다.
```

## Listing

```
git stash list #모든 stashes를 리스트로 보여줍니다.
git stash show hash #해쉬 stash의 내용을 보여줍니다.
git stash show hash -p #해쉬 스태쉬의 구체적인 내용을 보여줍니다.
```

## Applying

```
git stash apply hash #해쉬 stash를 다시 가져와서 적용합니다.(stash에는 그대로 남아있음)
git stash apply #해쉬 스태쉬를 지정하지 않으면 가장 마지막에 stash한 스태쉬를 가져와서 적용합니다.(stash에는 그대로 남아있음)
git stash pop #해쉬 stash를 가져와서 적용하고 stash에서 삭제합니다.
git stash branch branchName #새로운 브랜치를 만듬과 동시에 stash를 적용합니다.
```

## Deleting

```
git stash drop hash #해쉬 stash를 삭제합니다.
git stash clear #모든 stash를 삭제합니다.
```
