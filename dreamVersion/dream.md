# Dream Version

## Git 초기화하고 Github에 push하기

먼저 Github에 push하기 위해서는 Git WorkFlow 흐름에 대해서 정확히 알고 있어야 한다.<br>
![01-2](./Subject1/01-1.PNG)
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

## Git Workflow

![02-1](./Subject2/02-1.PNG)
Working Directory에는 2가지로 분류될 수 있습니다.<br>

1. 새로 만들어진 파일이어서 깃이 아직 track하지 않은 상태인 `Untracked` 상태
2. git add를 통해 깃이 이미 알고 있어 track중인 `tracked` 상태가 있습니다.
3. tracked는 또 2가지로 분류되는데 1번째는 이전버전과 현재버전에서 달라진 점이 없어 변경내역이 없는 `Unmodified` 상태
4. 수정이 되어 staging area로 이동할 수 있는 `modified` 상태가 있습니다.

이러한 흐름을 가지고 아래의 내용을 봅시다.

![02-2](./Subject2/02-2.PNG)

1. echo hellow world! > a.txt(b,c도 마찬가지)를 통해 txt파일 3개를 만듭니다.<br>
   이 파일들은 git이 아직 이러한 파일들이 있는지 인식하지 못해 untracked 상태입니다.
2. git add \*.txt 명령어를 통해 staging area로 옮깁니다. 이때부터 깃은 txt파일이 3개가 있다는 것을 인지합니다.<br>
   또한 위 사진에서 보듯이 커밋될 준비가 되어있는 파일이 3개 있다고 git status 명령어를 사용해 확인할 수 있습니다.<br>
3. 여기서 echo tsuel >> a.txt 명령어를 사용해 a텍스트파일에 내용을 추가하니 tracked에서 a.txt가 modified 상태가 된 것을 알 수 있습니다.<br>
   git status를 통해 확인해보면 아직 커밋될 준비가 되지않은 modified된 a.txt가 하나 존재하는 것을 알 수 있습니다.<br>