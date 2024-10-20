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
        git checkout "브랜치 이름"
        ```

<br>

- 지역 저장소 브랜치 생성
    - ```java
        git branch "브랜치 이름"
        ```

<br>

- 지역 저장소 브랜치를 원격 저장소에 반영
    - ```java
        // 새로운 로컬 브랜치를 원격 저장소에 푸시 하여, 원격에도 해당 브랜치를 생성
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

- 빨리감기 병합
    - ```java
        // fast-forward 브랜치에서 변경 파일 추가 및 커밋 후
        // main 브랜치를 작업 브랜치로 변경
        git branch test/fast-forward
        git checkout test/fast-forward
        
        git add .
        git commit -m "Chang title"
        
        git checkout main

        // fast-forward 브랜치를 main 브랜치에 병합
        git merge test/fast-forward
        ```

<br><br>

## 풀 리퀘스트 요청

<br>

- 풀 리퀘스트의 필요성
    - 여러 개발자가 함께 작업할 때 중요
    - 변경 내역이 프로젝트에 미치는 영향 확인 필요

<br>

- 풀 리퀘스트의 목적
    - 동료들에게 변경 내역 검토 요청
    - 기준 브랜치에 병합하기 전 피드백 수집

<br>

- GitHub의 지원
    - 풀 리퀘스트 기능 제공
    - 브랜치 병합 전 변경 내역 공유 및 검토 가능

<br>

<hr>

<br>

- 요청
    1. Pull requests
    2. New pull request
    3. base: "브랜치", compare: "브랜치" 선택
    4. 변경 내역 확인 후 Create pull request
    5. 풀 리퀘스트 내용 작성 후 Create pull request
- 검토
    1. Pull requests
    2. Review changes
    3. Submit review
- 병합
    - Merge pull request
    - Confirm merge
- 반영
    - git pull "원격 저장소 식별자" "원격 저장소 브랜치"
        - `git pull origin main`

<br><br>

## 협업 규칙

<br>

- 커밋 단위
    - 커밋의 최소 단위 유지
        - 큰 변경사항은 여러 개의 작은 커밋으로 나누기
        - 각 커밋은 atomic(원자적)하게 유지
    - 하나의 커밋에는 하나의 의도만 포함
        - 여러 파일을 수정하더라도 단일 목적 유지
        - 버그 수정이나 새 기능 추가 등 한 가지 의도로 제한
    - 단일 파일 수정 시에도 목적 분리
        - 하나의 파일에서 여러 변경사항 발생 시 커밋 분리
        - 버그 수정과 새 기능 추가를 별도의 커밋으로 구분

<br>

<hr>

<br>

- 커밋 메시지 작성
    - ```java
        "category" - "simple message"
        "detailed description"
        ```
        - |이름|설명|
            |-|-|
            |fix|잘못된 부분 수정|
            |add|기능 추가|
            |mod|코드 수정|
            |rm|기능 삭제|
    - ```java
        "type" : "message" ("issue number")
        ```
        - |이름|설명|
            |-|-|
            |fear|기능 추가|
            |fix|버그 수정|
            |docs|문서/주석 관련 작업|
            |refactor|리팩토링|
            |test|테스트 관련 작업|
            |chore|기타 작업|

<br>

<hr>

<br>

- 브랜치 이름 작성
    - ```java
        // new/feat-foo
        // new/fear-bar
        // bug/critical-thing
        // test/awesome-new-library
        "이름"/"..."
        ```
        - |이름|설명|
            |-|-|
            |new|새 기능 추가가 목적인 브랜치|
            |test|무언가를 테스트하는 브랜치<br>(새 라이브러리, 배포 환경, 실험 등)|
            |bug|버그 수정이 목적인 브랜치|

<br>

<hr>

<br>

- 버전 이름 작성 (버전 x.y.z)
    - x (Major 버전)
        - 기존 버전과 호환되지 않는 API 변경 시 증가
        - 대규모 리팩토링이나 아키텍처 변경 시 사용
    - y (Minor 버전)
        - 기존 버전과 호환되는 새로운 기능 추가 시 증가
        - 기존 기능에 대한 개선이나 확장 시 사용
    - z (Patch 버전)
        - 기존 버전과 호환되는 버그 수정 시 증가
        - 성능 개선이나 내부 구현 변경 등 사용자에게 영향이 없는 변경 시 사용

<br><br>

## 커밋 이력 조작

<br>

- `git cherry-pick`
    - 특정 상황에서 선택적 커밋 적용
        - 전체 브랜치 병합 대신 필요한 커밋만 선택
        - 작업 브랜치에 특정 커밋 추가 가능
    - 주요 사용 사례
        - 긴급 버그 수정 : 치명적 결함 수정 커밋만 운영 브랜치에 적용
        - 잘못된 브랜치 작업 정정 : 의도한 브랜치로 특정 커밋 이동
    - ```java
        // 다른 브랜치의 커밋을 작업 브랜치에 추가
        git cherry-pick "커밋 해시"
        ```

<br>

- `git reset`
    - ```java
        // 이전 커밋으로 작업 브랜치의 최종 커밋 변경
        git reset "커밋 해시"
        ```

<br>

- `git revert`
    - ```java
        // 변경 사항을 되돌림
        git revert "커밋 해시"
        ```

<br>

- `git rebase`
    - ```java
        // 커밋 이력을 재정렬
        git rebase "커밋 해시"
        ```
