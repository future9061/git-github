# 🎇목차

1. [👨‍💻 Git과 Github를 시작하며..](#-Git과-Github를-시작하며..)
2. [🔹 브랜치 구조](#-branch-구조)
3. [🔸 깃 저장소 ](#-깃-저장소)
4. [💬 git 초기화 및 커밋](#-git-초기화-및-커밋)
5. [✍ 원격 레포지토리에 연결 및 브랜치 관리](#-원격-레포지토리에-연결-및-브랜치-관리)
6. [😎 issue, PR 활용하기](#)

## 👨‍💻 Git과 Github를 시작하며..

> 처음으로 팀 프로젝트를 진행하며 어설프에 사용하던 깃과 깃허브의 순기능을 경험해보았다. <br /> 브랜치의 존재는 알고 있었지만 정확히 어떤 역할을 하는지 알지 못했고 때문에 그동안 메인 브랜치만 사용했었는데 이번에 브랜치 생성, 병합, 삭제 등 브랜치를 프로젝트에서 사용해보고 깃 그래프도 살펴보며 실무에서 사용하는 깃을 조금이나마 알 수 있었다고 생각한다.<br >
> 또, 깃허브가 생각보다 다양한 기능들을 가지고 있어 놀랐다. <br > 보드, 이슈, pr 등등.. 깃허브를 이용하여 프로젝트 진행 정도를 쉽게 볼 수 있고, 코드 리뷰를 통해 기록과 공부가 가능했다. <br > 이제까지는 아이패드로 스터디 플래너를 작성해왔는데 깃허브를 스터디 플래너로 사용 할 수 있을 것 같았다. 앞으로 깃과 깃허브를 자주 활용하여 경험치를 쌓기로 마음먹고 깃에 대한 정리를 해보았다.

<br />

## 🔹 Branch 구조

<img src="https://velog.velcdn.com/images/ssol_916/post/63a1ec26-777d-4346-91a5-f94ae102bbc2/image.webp">

_브랜치를 만들때 이와 같은 모양으로 만든다. 가장 직관적으로 브랜치의 모양을 잘 나타냈다고 생각한 이미지이다._ <br >

브랜치의 이름은 관습적으로 사용하는 것이 정해져있다.

- main
- develop
- feature (가장 작은 단위인 feature는 기능의 이름이나 작성한 사람의 이름을 붙이기도 한다.)

#### ❓ _왜 브랜치를 사용하는가?_

협업과 버전관리 때문이라고 생각한다.
<sub>_깃의 기능은 **버전관리, 백업, 협업** 이다._</sub> <br />
회사에서 프로젝트를 맡게 된다면 혼자가 아닌 팀으로 프로젝트를 진행하게 된다.
여러명이 작업을 해야 하기 때문에 main 브랜치에서 각자의 branch를 만들어 작업을 하며 병합을 하는 방식으로 개발을 하게 된다. <br />
그러던 도중
팀원 중 누군가가 프로젝트의 뿌리인 메인 브랜치에 검수하지 않은 코드를 merge 한다면 문제가 될 것이다. 때문에 main 브랜치 하위에 develop 브랜치, 그리고 develop 브랜치 하위에 feature 브랜치를 만들고, 제일 하위 브랜치에서 코드를 작성하고 검수하여 병합해가는 과정을 거친다. <br />
이로 인해 중요한 main 브랜치를 지킬 수 있는 과정을 구축했다고 생각한다.
또한 배포한 프로젝트여도 기능 추가, 버그 해결 등의 코드 수정은 계속되기 때문에 이후에 버전 관리를 위해서도 사용된다. <br >
나는 단순히 브랜치를 나누고 병합해가는 것만 경험해봤기 때문에 출시 버전을 위한 Release Branch나 출시 전 발생한 버그를 수정하는 Hotfix Branch는 나중에 리뷰를 남기려고 한다.

<br >

## 🔸 깃 저장소

> 깃을 사용하다 보면 자주 만나게 되는 메세지들이 있다. <br >
> working tree 라던지 untracked file 같은 생소한 단어들이다.<br >
> 이것은 깃 저장소와 관련되어 있기 때문에 깃이 어떻게 파일을 저장하고 삭제하며 그 모든 내역을 기록할 수 있는지 깃의 저장 과정에 대해 적어본다.<br >

#### ✔ 작업 트리

깃에 있는 파일이 저장되어 있는 directory이다. working tree라고 부른다.<br>
처음 작업 트리에서 `git init`을 하면 숨겨진 .git 폴더가 생기는데 이 폴더에 스테이지와 저장소가 생긴다.

#### ✔ 스테이지

staging area라고 한다. `git add`를 실행했을 시 파일이 저장되는 공간이다.<br>
최종 저장 전 잠시 파일이 대기하는 공간이라고 생각하면 된다.

#### ✔ 저장소

repository로 최종적으로 파일이 저장되는 저장소이다. 깃 허브에 만드는 reporitory가 이것이다.

   <br >

1. 처음 로컬에서 코드를 작성하면 파일은 작업 트리에만 존재한다.
   <img src="https://github.com/future9061/git-github/assets/132829711/c4a23d3c-2d0c-4220-9507-3304c1fb9b7d">

2. git add로 파일을 stage에 대기 시켜놓는다.
   ![image](https://github.com/future9061/git-github/assets/132829711/68b2dbbd-0c53-4a76-be7b-f8f8b509c788)

3. 마지막에 git commit으로 로컬 저장소나 push로 원격 저장소에 파일을 저장하면 최종 저장이 완성된 것이다.
   ![image](https://github.com/future9061/git-github/assets/132829711/e1f6782c-7fa3-46fe-a601-f807b428911b)

 <br >

## 💬 git 초기화 및 커밋

#### ➰ 처음 프로젝트를 시작할 때 거치는 과정이다.

<br />

✔ `git init`

<img src="https://github.com/future9061/coffeebean-mobile/assets/132829711/fafb732e-b7f9-401f-88de-c52284ea4404" /> <br />

디렉토리에서 git을 사용하기 위해 git init으로 초기화한다. <br />
_초기화를 하면 상단에 (main)이 생긴것을 확인 할 수 있다. main branch가 생긴것이다._

<br >

✔ `git add .`

<img src="https://github.com/future9061/coffeebean-mobile/assets/132829711/803eb201-2328-4568-9672-2b3835a0a289" /> <br />
파일을 저장소에 올리기 전 stage에 대기시킨다. <br >
`git status`를 통해 add 된 파일 목록을 확인한다.

<br >

✔ `git commit -m 'message'`

<img src="https://github.com/future9061/git-github/assets/132829711/098ccd1c-7395-4ccf-83c6-88ea0b9e9d21" /> <br />
최종 저장소에 저장한다. `git log`를 통해 커밋 이력 확인 및 수정도 가능하다. <br> 이제 로컬 최종 저장소에는 파일이 저장됐다!
<br >

## ✍ 원격 레포지토리에 연결 및 브랜치 관리

#### ➰이제 원격 레포지토리(깃허브)에 코드를 올리고 협업과 버전관리를 위해 브랜치를 만들어보는 단계이다.

✔ `git remote add origin url`

<img src="https://github.com/future9061/coffeebean-mobile/assets/132829711/b81d179f-82c8-4b97-ac17-f36c5dc05859" /> <br />

원격 레포지토리의 url을 가져와서 연결한다. <br>
이 명령어에서 origin은 원격 레포지토리의 이름을 명명하는 것이다. <br />
관습적으로 origin이라고 부른다.

<br >

✔ `git push origin +main`
![image](https://github.com/future9061/git-github/assets/132829711/420d66d8-250d-48e8-bc77-aa728f9a4ac6) <br />
첫 push시에는 원격 저장소와 로컬 저장소가 관련이 없다고 생각한 git이 push를 거부한다.<br /> 때문에 +main으로 강제로 push를 해야한다.

<details><summary>⭐참고
</summary>
<img src="https://github.com/future9061/git-github/assets/132829711/badd7be0-e721-443c-b366-2dd88046b91e"> <br />
오리진은 모든 팀원이 사용하는 저장소이기 때문에 계속 push가 일어난다. <br>
때문에 push 전에는 pull이나 fetch로 원격과 같은 환경을 맞춰주는 과정이 필요할 수도 있다.

</details>

<br>

![image](https://github.com/future9061/git-github/assets/132829711/7bbcba56-ee7e-4c44-b98c-6bed29dd2b1d)<br />
_원격 레포지토리에 잘 올라갔다!_

<br >

#### ➰방금까지의 과정은 원격 레포지토리와 로컬 레포지토리를 연결 하고 첫 push하는 과정이였다. <br />
이제 팀 프로젝트를 시작했다는 가정 하에 원격 레포지토리를 가져와서 내 작업 브랜치를 만들어 작업을 해보겠다.

![image](https://github.com/future9061/git-github/assets/132829711/6f8eea86-8668-451d-96ba-2ae2bbb00907) <br>
_main 브랜치는 건드려서는 안되고 develop 브랜치를 가져와 feature를 만들어서 코드를 작성해야 한다._

<br>

✔ `git pull origin develop`
![image](https://github.com/future9061/git-github/assets/132829711/106a5ae3-2b1c-4b0b-a112-12971c6bd742) <br />
develop 브랜치를 가져왔다. <br >
상단에 (develop)가 아니고 (main)이라면 `git checkout develop`로 브랜치를 이동해야한다.

✔ `git branch feature`  <br />
![image](https://github.com/future9061/git-github/assets/132829711/efbe3abe-3fe6-4c41-ae1a-4d52ed50cc10) <br />
feature 브랜치를 만들었다. 현재 로컬에 main, branch, feature 세 개의 브랜치가 존재한다.

✔ `git checkout feature`  <br />
![image](https://github.com/future9061/git-github/assets/132829711/9cff3c83-5e90-47d5-b949-8f35de4fd09f) <br />
feature 브랜치로 이동 후 코드를 작성한다.

✔ `git push origin feature`  <br />
![image](https://github.com/future9061/git-github/assets/132829711/ecf8f3c4-f3a0-442a-9563-23be44cb3f00) <br />

이제 feature가 원격 레포지토리에 생겼다.

![image](https://github.com/future9061/git-github/assets/132829711/544d4050-3a71-4778-b06a-d936ce1870c3) <br />

그럼 PR 버튼이 나오는데 코드 검수 후 develop 브랜치에 병합해주면 끝!<br />
아쉽게도 나는 md 파일만 올려서 Your main branch isn't protected로 PR이 뜨진 않았다.
다음 프로젝트에서 PR과 issue 사용, 그리고 보드 활용해서 프로젝트 진행상황 확인하는 작업을 리뷰로 남기도록 하겠다!
