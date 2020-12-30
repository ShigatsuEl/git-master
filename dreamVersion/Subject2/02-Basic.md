# Basic

## Git init

```
git init #깃 저장소를 생성
rm -rf .git #깃 저장소 삭제
```

## Show the Working Tree Status

깃에서 작업하면서 현재 어떤 구조로 저장되어있는지 모든 파일에 대해 확인할 수 있다.

```
git status #모든 status를 출력함
git status -s #짧게 간추려서 status를 출력함
```

## Ignoring Files

무시하고 싶은 파일을 .gitignore에 추가하면 트래킹하지 않습니다.

```
# .a 파일들을 전부 무시합니다.
*.a
# 위에서 .a 파일들을 전부 무시해도 lib.a 파일은 트래킹합니다.
!lib.a
# TODO 파일을 무시합니다.(현재 디렉토리에 있는)
/TODO
# bulid dir안에 있는 파일들을 전부 무시합니다.
build/
# doc dir 안에 있는 모든 txt파일들을 무시합니다.(하위 dir는 제외)
doc/*.txt
# doc dir 안에 있는 모든 pdf파일들을 무시합니다.(하위 dir 포함)
doc/**/*.pdf
```

## Staging Files

```
git add a.txt #a.txt 파일을 staging area로 옮깁니다.
git add a.txt b.txt #a.txt와 b.txt 파일을 staging area로 옮깁니다.
git add *.txt #.txt로 끝나는 모든 파일들을 staging area로 옮깁니다.
git add * #삭제된 파일들과 .으로 시작하는 파일들을 제외한 나머지를 staging area로 옮깁니다.
git add . #모든 것을 staging area로 옮깁니다.
```

## Modifying File

### Removing Files

```
rm file.txt #file.txt를 삭제합니다.
git add file.txt #file.txt를 staging area로 옮깁니다.
git rm file.txt #file.txt를 staging area에서 제거함과 동시에 working dir에서도 제거합니다.
git rm --cached file.txt #staging area에서 제거합니다.
git clean -fd #untrack된 파일들을 모두 제거합니다.
```

### Moving Files

```
git mv from.txt to.txt
git mv from.text /logs/from.text #전자 파일을 후자 위치로 이동한다.
```

## Viewing the Staged/Unstaged changes

```
git status # 깃의 상태를 전체적으로 볼 수 있다.
git status -s #깃의 상태를 전체적으로 보되, 단축해서 보여줍니다.
git diff # Working directory의 바뀐 부분을 보여줍니다,
git diff --staged # Staged Area의 바뀐 부분을 보여줍니다.
git diff --cached # Staged Area의 바뀐 부분을 보여주는 또 다른 명령어 입니다.
```

## Visual Diff Tool

### Open .gitconfig and add below

```
difftool을 사용하기 위해 git config --global -e를 사용해 설정을 바꿔주어야 합니다.
[diff]
  tool = vscode
[difftool "vscode"]
  cmd = code --wait --diff $LOCAL $REMOTE
```

### Run Diff Tool

```
git difftool // difftool을 실행합니다.
```

## Commit

```
git commit #staged된 파일들을 커밋합니다.
git commit -m "Commit message" # 커밋메시지와 함께 staged 파일들을 커밋합니다.
git commit -am "Commit message" # git add .을 생략하고도 git commit -am을 통해 한번에 커밋메시지와 함께 커밋할 수 있습니다.
```

## Log & History

### See History

```
git log #커밋 리스트를 볼 수 있습니다.
git log --patch #각 커밋 사이의 다른 점을 볼 수 있다.
git log -p #--patch의 shortcut
git log --state #abbreviated states for each commit
git log --oneline #커밋 리스트를 한줄로 볼 수 있다.
git log --oneline --reverse #커밋 리스트를 가장 첫번째에 한 것부터 순서대로 볼 수 있다.(한 줄로)
```

### Filtering

```
git log -2 #가장 최신 커밋으로부터 2개의 커밋을 보여줌
git log --author="ellie" #작성자가 ellie인 커밋만 보여줌
git log --before="2020-09-29" #2020-09-29이전의 커밋을 보여줌
git log --after="one week ago" #일주일 전 이후의 커밋을 보여줌
git log --grep="message" #message라는 이름을 가진 커밋을 찾아서 보여줌
git log -S="code" #코드 내에 code가 들어있는 커밋을 보여줌
git log file.txt #file.txt에 관련된 커밋들만 보여줌
```

### History of a File

```
git log file.txt #file.txt의 기록을 보여줌
git log --state file.txt #file.txt의 상태만 보여줌
git log --patch file.txt #file.txt의 변화된 부분을 보여줌
```

### HEAD & Hash Code

```
git log HEAD #HEAD부터 커밋 리스트를 보여줌
git log HEAD~1 #HEAD 이전의 커밋부터 커밋 리스트를 보여줌
git log hash #해쉬코드 커밋 이전부터 커밋 리스트를 보여줌
```

### Viewing a commit

```
git show HEAD #HEAD 커밋을 상세하게 보여줍니다.
git show hash #해쉬 코드의 커밋을 상세하게 보여줍니다.
git show hash:file.txt #해쉬코드의 커밋 중 file.txt에 해당하는 부분만 보여줍니다.
```

### Comparing

```
git diff hash1 hash2 #두 커밋 사이의 다른 점을 상세하게 보여줌
git diff hash1 hash2 file.txt #두 커밋 사이에서 file.txt의 다른 부분을 보여줌
```

## Tagging

### Creating

```
git tag v1.0.0 #마지막 커밋에 태그를 붙입니다.
git tag v1.0.0 hash #특정 커밋에 태그를 붙입니다.
git show v1.0.0 #특정 태그를 상세하게 보여줍니다.
git tag -a v.1.0.0 -m "message" #태그에 설명을 붙일 수 있습니다.
```

### Listing

```
git tag #모든 태그를 리스트로 보여줍니다.
git tag -l "v1.0.*" #버전 1.0으로 시작하는 모든 태그를 리스트로 보여줌
```

### Deleting

```
git tag -d v1.0.0 #특정 버전의 태그를 삭제합니다.
```

### Syncing with Remote

```
git push origin v1.0.0 #특정 태그를 원격 저장소에 푸쉬
git push origin --tags #모든 태그들을 원격 저장소에 푸쉬
git push origin --delete v1.0.0 #특정 커밋을 원격 저장소에서 삭제
```

### Checking out Tags

```
git checkout v1.0.0 #특정 태그로 이동합니다.(HEAD는 특정 태그가 됨)
git checkout -b branchName v1.0.0 #특정 태그로부터 브랜치를 생성합니다.
```

[(C)Dream Coding Academy](https://academy.dream-coding.com/)
