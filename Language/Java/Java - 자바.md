# Java - 자바

# 자바 표준 스펙

## 자바 표준 스펙과 구현

- 자바는 표준 스펙과 구현으로 나눌 수 있음.
  - 자바 표준 스펙
    - 자바는 이렇게 만들어야 한다는 설계도이며, 문서임.
    - 이 표준 스펙을 기반으로 여러 회사에서 실제 작동하는 자바를 만듦.
    - 자바 표준 스펙은 자바 커뮤니티 프로세스(JCP)를 통해 관리함.
  - 다양한 자바 구현
    - 여러 회사에서 자바 표준 스펙에 맞추어 실제 작동하는 자바 프로그램을 개발함.
    - 각각 장단점이 있음.
    - 윈도우, MAC, 리눅스 같이 다양한 OS에서 작동하는 버전의 자바를 함께 제공함.

------

- 자바 구현들은 모두 표준 스펙에 맞도록 개발되어 있음.
- 오라클 Open JDK를 사용하다가 Amazon Corretto 자바로 변경해도 대부분 문제 없음.

## 컴파일과 실행

- 자바 프로그램은 컴파일과 실행 단계를 거침.
  - Hello.java와 같은 자바 소스 코드를 개발자가 작성함.
  - 자바 컴파일러를 사용해서 소스 코드를 컴파일 함.
    - 자바가 제공하는 javac라는 프로그램을 사용함.
    - .java → .class 파일이 생성됨.
    - 자바 소소 코드를 바이트코드로 변환하며 자바 가상 머신(JVM)에서 최적화하고 문법 오류도 검출함.
  - 자바 프로그램을 실행함.
    - 자바가 제공하는 java라는 프로그램을 사용함.
    - JVM이 실행되면서 프로그램이 작동함.

### 자바 프로그램

- 자바 프로그램은 자바가 설치된 모든 OS에서 실행할 수 있음.
- 자바 개발자는 특정 OS에 맞추어 개발을 하지 않아도 됨. (자바에 맞추어 개발하면 됨.)
- OS 호환성 문제는 자바가 해결함. Hello.class와 같이 컴파일된 자바 파일은 모든 자바 환경에서 실행할 수 있음.
- 윈도우 자바는 윈도우 OS가 사용하는 명령어들로 구성되어 있음.
- MAC이나 리눅스 자바도 본인의 OS가 사용하는 명령어들로 구성되어 있음.

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194541