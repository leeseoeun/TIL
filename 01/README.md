**01. Gradle 빌드 도구를 활용한 자바 프로젝트 구성**

<br>

```
프로젝트 폴더
└─ src
    ├─ main          애플리케이션 관련 파일을 두는 폴더
    │  ├─ java      패키지 폴더 및 자바 소스 파일(.java)
    │  └─ resources 패키지 폴더 및 설정 파일(.xml, .properties 등)
    │  └─ webapp    웹 파일(HTML, CSS, JavaScript, JPEG, JSP 등)
    └─ test          단위 테스트 관련 파일을 두는 폴더
        ├─ java      패키지 폴더 및 단위 테스트 자바 소스 파일
        └─ resources 단위 테스트 관련 설정 파일(.xml, .properties 등)
```

<br>

*console*

```console
[~]$ mkdir TIL
[~]$ cd TIL
```

```console
[~/TIL]$ gradle init
Starting a Gradle Daemon (subsequent builds will be faster)

Select type of project to generate:
  1: basic
  2: application 프로젝트 유형
  3: library
  4: Gradle plugin
Enter selection (default: basic) [1..4] 2

Select implementation language:
  1: C++
  2: Groovy
  3: Java 프로그래밍에 사용할 언어
  4: Kotlin
  5: Swift
Enter selection (default: Java) [1..5] 3

Select build script DSL:
  1: Groovy 빌드 스크립트 파일을 작성할 때 사용할 언어
  2: Kotlin
Enter selection (default: Groovy) [1..2] 1

Select test framework:
  1: JUnit 4 단위 테스트로 사용할 프레임워크
  2: TestNG
  3: Spock
  4: JUnit Jupiter
Enter selection (default: JUnit 4) [1..4] 1

Project name (default: TIL): (엔터: 현재 디렉토리명을 프로젝트 이름으로 사용)
Source package (default: TIL): 기본 자바 패키지 설정
```

<br>

*builde.gradle*

```
plugins {
    // Apply the application plugin to add support for building a CLI application in Java.
    id 'eclipse'
}

eclipse {
    project {
        name = "baekjoon"
    }
}
```

<br>

*console*

```console
[~/TIL/app]$ gradle eclipse
[~/TIL/app]$ gradle cleanEclipse
```
