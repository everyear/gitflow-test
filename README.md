# gitflow-test

clone 후 각자 로컬에서 시험해보기, push 하지 말아주세요 

<br>

# 레파지토리 clone
```
git clone https://github.com/everyear/gitflow-test.git
```

<br>

# git-flow 설치 
MAC OS 
```
brew install git-flow-avh
```

Ubuntu 
```
apt-get install git-flow
```

설치 참고 : https://soft.plusblog.co.kr/20

<br>

# git flow 시작
git-flow를 사용하기 위해서 초기화가 필요  
git init과 같은 방식이라고 생각하면 됨. 

git flow init을 할 경우 기본적으로 생성되는 브랜치들의 이름을 커스터 마이징할 수 있다.  
기본적인 브랜치의 이름을 그대로 사용하고 싶다면 -d 옵션을 주면 그대로 생성됨
```
git flow init -d
```
<img width="655" alt="image" src="https://user-images.githubusercontent.com/74139156/160324016-8c523da5-12b1-49bc-a6a8-cae7fec86597.png">


git flow init으로 생성되는 브랜치는 6종류 

- master : 사용자에게 배포되는 Stable 브랜치
- develop : 다음 릴리즈를 위해 기능들을 모으는 최신 브랜치
- feature : 특정 기능 개발을 위한 브랜치
- release : 릴리즈를 위해 버그 픽스(Bug fix)를 모으는 브랜치
- hotfix : 긴급 버그 픽스를 위한 브랜치
- support : 버전 호환성 문제를 위한 브랜치

Version tag prefix는 master 브랜치로 릴리즈 버전이 병합될 때 생성되는 태그(Tag)의 프리픽스(Prefix)를 설정할 수 있는 선택 항목이다. 

# feature : 기능 개발하기 

특정 기능을 개발하기 위한 개발 브랜치를 다루기 위한 명령어  

```
git flow feature start first_feature
```
<img width="711" alt="image" src="https://user-images.githubusercontent.com/74139156/160324118-ca0ecaa3-c56f-47c0-acd1-2656ab7fe6ef.png">

위의 명령을 수행하면 develop 브랜치로 부터 갈라져 나온 새로운 feature 개발 브랜치가 생성되며 자동으로 해당 branch로 checkout 된다. 생성된 브랜치는 feature/<feature_name>으로 이름이 지정된다.

기존에 다음처럼 사용하던 명령어를 대체하는 명령어 (아래는 실행 X, 기존에 사용하는 방법)
```
git checkout -b feature/<feature_name>
```

# feature : 기능 개발완료 후  

```
git flow feature finish first_feature
```
<img width="834" alt="image" src="https://user-images.githubusercontent.com/74139156/160324554-33b6f91d-fbed-48c6-94b3-bc7410ac7599.png">

개발이 끝난후 위 명령어를 수행하면 git-flow가 자동으로 develop branch로 checkout 한 다음 작업하던 feature brnach 변경사항을 merge하게 된다. merge완료 후 해당 branch를 삭제 한다. 

git flow 사용전
```
git checkout develop 
git merge feature/first_feature
git branch -d feature/first_feature
```

# feature : 개발중이 feature push & pull(원격에 공유하기, 가져오기)

```
git flow feature publish feature_name
```
이 명령을 수행하면 origin으로 설정된 원격 저장소로 브랜치를 Push 한다.
```
git flow feature pull origin feature_name
```
