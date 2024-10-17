# Git & GitHub

<br>

## Git 설치

<br>

- 기본 브랜치가 master로 되어 있기 때문에 main으로 변경해야 됨
    - ```java
        // 윈도우
        Git 설치 시
        "Adjusting the name of the initial branch in new repositories" 에서
        "Override the default branch name for new repositories" 체크 후
        "main" 입력

        // 리눅스, 맥 OS
        git config --global init.defaultBranch main
        ```

<br><br>

## GitHub 둘러보기

<br>

- Projects
    - 사용자가 관리하는 <b>프로젝트 보트</b> 확인

<br>

- Packages
    - 사용자가 만든 <b>소프트웨어 패키지</b> 저장 및 배포

<br><br>

## 지역 저장소에 커밋하기 (= 로컬 저장소)

<br>

- Git 초기화
    - ```java
        // 새로운 Git 저장소 생성 또는 기존 Git 저장소 초기화
        git init
        ```
        - Git 저장소를 생성하지 않으면 Git 명령어를 사용할 수 없음

<br>

- Git 사용자 설정
    - ```java
        // --global을 사용하면 전역으로 설정 가능
        git config user.name "이름"
        git config user.eamil "이메일"
        ```

<br><br>

## 원격 저장소에 커밋하기

<br>

- 개인용 액세스 토큰 발급
    1. Settings
    2. Developer settings
    3. Personal access tokens
    4. Tokens (classic)
    5. Generate new token (classic)
    6. Generate token

<br>

- 원격 저장소의 주소 등록
    - ```java
        git remote add origin "주소"
        ```

<br><br>

## 지역 저장소 생성

<br>

- 취소
    - ```java
        // .git 디렉토리와 그 하위 모든 파일 강제로 삭제
        rm -rf .git
        ```
    - 윈도우는 Git Bash에서 사용할 수 있음
        - 아래 명령어들은 Git Bash에서 사용

<br><br>

## 환경 설정

<br>

- Git 설정 파일 확인
    - ```java
        cat .git/config
        ```

<br>

- |Untracked 상태|Tracked 상태|||
    |-|-|-|-|
    |작업 디렉터리에 있는 상태<br>Git이 추적하지 않는 파일의 상태|스테이징 영역, 지역 저장소에 있는 상태<br>Git이 추적하고 있는 파일의 상태|
    |git  add를 하지 않은 상태|git add, git commit을 한 상태|
    ||<b>Unmodified 상태</b>|<b>Modified 상태</b>|
    ||가장 최근 커밋 또는 스테이징된 상태와 동일하여 수정되지 않은 상태|Git이 추적하는 파일이 수정된 상태|
    - git status로 확인할 수 있음

<br><br>

## 커밋 생성 후 푸시

- git commit만 입력 시 에디터를 열어 커밋 메시지를 입력할 수 있음
    - i : 입력
    - :wq : 저장 후 종료

<br>

- 커밋 메세지 및 저자 수정 방법
    - ```java
        // 에디터를 열어 커밋 메시지를 수정할 수 있음
        git commit --amend

        // 터미널에서 바로 커밋 메시지를 입력하여 수정할 수 있음
        git commit --amend -m "메시지"

        // 커밋 메시지를 그대로 유지하면서 커밋의 내용을 업데이트 할 수 있음
        git commit --amend --no-edit

        // 커밋 저자를 수정할 수 있음
        git commit --amend --author "이름 <이메일>"
        ```

<br>

- 커밋 로그 확인 방법
    - ```java
        // 파일 단위로 변경 사항을 확인할 수 있음
        git log -p

        // 커밋 로그를 한 줄로 요약하고, 그래프로 커밋 흐름을 파악할 수 있음
        git log --pretty=oneline --graph
        ```

<br>

- HEAD
    - 최종 커밋을 가리키는 포인터


<br><br>

## 프로젝트 소개

<br>

- Node.js
    - 자바스크립트 실행을 위한 런타임 환경
    - npm(Node Package Manager)이 함께 설치됨

<br>

- Express.js
    - Node.js 실행을 위한 웹 애플리케이션 프레임워크
    - express-generator를 통해 프로젝트 생성 가능

<br><br>

## 프로젝트 실습 환경 구축

<br>

- Express.js 설치
    - ```java
        // 윈도우
        npm install express-generator -g

        // 리눅스, 맥 OS
        sudo npm install express-generator -g
        ```

<br>

- Node.js 웹 애플리케이션 생성
    - ```java
        // --no-view : 템플릿 엔진을 포함하지 않음
        express "프로젝트 이름" --no-view
        ```

<br><br>

## Git 지역 저장소 및 초기 파일 설정

<br>

- 작업 순서 흐름도
    - ```java
        [git init]          // 깃 / 지역 환경 작업
            | 깃 지역 저장소 생성
            v
        [git config]        // 깃 / 지역 환경 작업
            | 깃 사용자 등록
            v
        [원격 저장소 생성]  // 깃허브 / 원격 작업 환경
            |
            v
        [git remote add]    // 깃 / 지역 환경 작업
            | 원격 저장소 등록
            v
        [.gitignore]        // 깃 / 지역 환경 작업
            | 깃 파일 등록
            v
        [git commit]        // 깃 / 지역 환경 작업
            | 깃 커밋 생성
            v
        [git push]          // 깃 / 지역 환경 작업
            |
            v
        [깃 커밋 반영]
        ```

<!--

<br><br>

## 브랜치 생성

<br>

- 지역 저장소 상태 갱신
    - ```java
        // 원격 저장소의 변경 사항을 로컬에 가지고 옴
        // 원격 저장소의 모든 브랜치와 태그 정보를 로컬의 원격 추적 브랜치에 업데이트
        git remote update
        ```

<br>

- 지역 저장소로 브랜치 가져오기
    - ```java
        // 원격 저장소의 특정 브랜치를 기반으로 로컬 브랜치를 생성하고, 해당 브랜치로 체크아웃
        git checkout -t origin/"브랜치 이름"
        ```

<br>

- 브랜치 확인
    - ```java
        // 모든 저장소 (로컬 및 원격)
        git branch -a

        // 지역 저장소
        git branch -l
        ```

<br>

- 작업 브랜치 변경
    - ```java
        // 작업 브랜치를 main 브랜치로 변경
        git checkout main
        ```

<br>

- 지역 저장소 브랜치 생성
    - ```java
        git branch "브랜치 이름"
        ```

<br>

- 지역 저장소 브랜치를 원격 저장소에 반영
    - ```java
        // 새로운 로컬 브랜치를 원격 저장소에 푸시하여, 원격에도 해당 브랜치를 생성
        git push origin "브랜치 이름"
        ```

<br>

- 브랜치 삭제
    - ```java
        // 지역 저장소
        git branch -d "브랜치 이름"

        // 원격 저장소
        git push origin -d "브랜치 이름"
        ```

<br><br>

## 브랜치 병합

<br>

- 

-->
