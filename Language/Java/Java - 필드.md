# 필드
- 필드는 객체의 고유 데이터, 객체가 가져야 할 부품, 객체의 현재 상태 데이터를 저장하는 곳입니다.
- 필드 선언은 클래스 중괄호 {}블록 어디서든 존재할 수 있습니다.
- 생성자 선언과 메소드 선언의 앞과 뒤 어떤 곳에서도 필드 선언이 가능합니다.
- 생정자와 메소드 중괄호 {} 블록 내부에는 선언될 수 없습니다.
#### 자동차 객체
- 고유 데이터
	- 제작회사 
	- 모델
	- 색깔
	- 최고 속도
- 상태 데이터
	- 현재 속도
	- 엔진 회전 수
- 부품
	- 차체
	- 엔진
	- 타이어
#### 자동차 클래스
```java
public class Car {

    String company;
    String model;
    String color;
    int maxSpeed;

    int speed;
    int rpm;

    Body body;
    Engine engine;
    Tire tire;
}
```
### 필드 선언
```java
타입 필드 [ = 초기값];

// Ex
String company = "현대자동차";
String model = "그랜저";
int maxSpeed = 300;
int productionYear;
int currentSpeed;
boolean engineStart;
```
- 타입 필드에 저장할 데이터의 종류를 결정합니다.
	- 타입에는 기본 타입과 참조 타입(배열, 열거, 인터페이스)이 모두 올 수 있습니다.
### 필드 사용
- 클래스 내부의 생성자와 메소드에서 바로 사용이 가능하나, 클래스 외부에서 사용할 경우에는 반드시 객체를 생성하고 참조 변수를 통해 사용해야 합니다.
