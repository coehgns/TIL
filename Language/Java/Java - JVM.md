# JVM
- 자바를 실행하기 위한 **가상 기계**(컴퓨터)라고 할 수 있습니다.
- JVM이라는 **가상 머신**을 거쳐서 JVM이 인식할 수 있는 `Java bytecode`로 변환됩니다.
# JVM 구성 요소
## 클래스 로더
- JVM 내로 클래스 파일을 로드하고 링크를 통해 배치하는 작업을 수행하는 모듈입니다.

---
## 실행 엔진
- 클래스를 실행 시키는 역할을 합니다.
#### 실행 엔진 - 인터프리터
- 자바 바이트 코드를 명령어 단위로 읽어서 실행합니다.
#### 실행 엔진 - JIT(Just-In-Time)
- 런타임 시 바이트 코드를 원시 시스템 코드로 컴파일하여 Java 애플리케이션의 성능을 향상시키는 런타임 환경의 컴포넌트입니다.
#### 실행 엔진 - 가비지 콜렉터
- 더 이상 사용되지 않는 인스턴스를 찾아 메모리에서 삭제합니다.

---
## 런타임 데이터 영역
- 프로그램을 수행하기 위해 OS에서 할당 받은 메모리 공간입니다.

## 참고 자료
- https://www.ibm.com/docs/ko/sdk-java-technology/8?topic=reference-jit-compiler
- https://doozi0316.tistory.com/entry/1%EC%A3%BC%EC%B0%A8-JVM%EC%9D%80-%EB%AC%B4%EC%97%87%EC%9D%B4%EB%A9%B0-%EC%9E%90%EB%B0%94-%EC%BD%94%EB%93%9C%EB%8A%94-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%8B%A4%ED%96%89%ED%95%98%EB%8A%94-%EA%B2%83%EC%9D%B8%EA%B0%80