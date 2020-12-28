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
