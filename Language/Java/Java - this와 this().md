# this 참조 변수
- this 참조 변수는 인스턴스가 바로 자기 자신을 참조하는 데 사용하는 변수입니다.
	- 이러한 this 참조 변수는 해당 인스턴스의 주소를 가리키고 있습니다.
```java
// 예제

class Car {
    private String modelName;
    private int modelYear;
    private String color;
    private int maxSpeed;
    private int currentSpeed;

	Car(String modelName, int modelYear, String color, int maxSpeed) {

        this.modelName = modelName;

        this.modelYear = modelYear;

        this.color = color;

        this.maxSpeed = maxSpeed;

        this.currentSpeed = 0;

    }

    ...
}
```
- 위 예제 처럼 생성자의 매개변수 이름과 인스턴스 변수의 이름이 같을 경우에는 인스턴스 변수 앞에 this 키워드를 붙여 구분해야 합니다.
- this 참조 변수를 사용하여 인스턴스 변수에 접근할 수 있습니다.
- this 참조 변수는 클래스 메소드에서는 사용할 수 없습니다.

# this() 메소드
- this() 메소드는 생성자 내부에서만 사용할 수 있으며, 같은 클래스의 다른 생성자를 호출할 때 사용합니다.
- this() 메소드에 인수를 전달하면 생성자 중에서 메소드 시그니처가 일치하는 다른 생성자를 찾아 호출해 줍니다.
	- 메소드 시그니처 : 메소드의 이름과 메소드의 원형에 명시되는 매개 변수 리스트를 가리킵니다.
```java
// 예제

class Car {
    private String modelName;
    private int modelYear;
    private String color;
    private int maxSpeed;
    private int currentSpeed;

	Car(String modelName, int modelYear, String color, int maxSpeed) {

        this.modelName = modelName;

        this.modelYear = modelYear;

        this.color = color;

        this.maxSpeed = maxSpeed;

        this.currentSpeed = 0;
}

	Car() {
		this("소나타", 2012, "검정색", 160);  // 다른 생성자 호출
	}

	public String getModel() {
		return this.modelYear + "년식" + this.modelName + this.color;
	}
}

public class Method05 {

    public static void main(String[] args) {

        Car tcpCar = new Car(); System.out.println(tcpCar.getModel());

    }

}
```
- 위 예제에서 매개변수를 가지는 첫 번째 생성자는 this 참조 변수를 사용하여 인스턴스 변수에 접근하고 있습니다.
- 매개변수를 가지지 않는 두 번째 생성자는 내부에서 this() 메소드를 이용하여 첫 번째 생성자를 호출합니다.

## 참고 자료
- https://www.tcpschool.com/java/java_methodConstructor_this