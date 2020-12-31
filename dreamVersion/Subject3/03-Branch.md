# Branch

## Creating branch

브랜치를 만드는 방법은 여러가지가 있다. 편한 방법을 고르면 된다.

```
git branch testing #testing 브랜치를 생성
git checkout testing #testing 브랜치로 스위치
git switch testing #testing 브랜치로 스위치(위와 같음)
git checkout -b testing #testing 브랜치를 만들고 스위치
git switch -C testing #testing 브랜치를 만들고 스위치(위와 같음)
```

## Managing Branch

```
git branch #모든 브랜치들의 리스트를 보여줌
git branch -r #원격 저장소들의 브랜치 리스트를 보여줌
git branch --all #로컬과 원격 저장소들의 브랜치 리스트를 보여줌
git branch -v #브랜치 각각의 최신 커밋들만 보여줌(의미없음)
git branch --merged #merged된 브랜치들을 보여줌
git branch --no-merged #merge되지 않은 브랜치들을 보여줌
git branch -d testing #testing 브랜치를 삭제
git push origin --delete testing #원격 저장소에 있는 testing 브랜치를 삭제
git branch --move wrong correct #로컬에 있는 브랜치 이름을 wrong -> correct로 바꿈
git push --set-upstream origin correct #원격 저장소에 있는 브랜치 이름은 wrong -> correct로 바꿈(위에가 먼저 발생해야 가능한 듯!)
```

## Comparing

```
git log branch1..branch2 #branch1과 branch2의 다른 커밋들을 보여줌
git diff branch1..branch2 #branch1과 branch2의 다른 내용들을 보여줌
```

## Merge

```
git merge featureA #현재 있는 브랜치에 featureA브랜치를 merge함
git merge --no-ff featureA #fast forward로 merge하지 않고 merge commit을 남김
```
