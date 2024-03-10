# Java - Annotation

# 어노테이션(Annotation)

- 어노테이션은 다른 프로그램에게 유용한 정보를 제공하기 위해 사용되는 것.
- 주석과 같은 의미를 가짐.

## 어노테이션의 역할

- 컴파일러에게 문법 에러를 체크하도록 정보를 제공함.
- 프로그램을 빌드할 때 코드를 자동으로 생성할 수 있도록 정보를 제공함.
- 런타임에게 특정 기능을 실행하도록 정보를 제공함.
- `@`을 사용하여 작성하며, 해당 타겟에 대한 동작을 수행하는 프로그램 외에는 다른 프로그램에게 영향을 주지 않음.

## 어노테이션 종류

- 자바에서 기본적으로 제공하는 **표준 어노테이션**

- 어노테이션을 정의하는 데 사용되는 **메타 어노테이션**

- **사용자 어노테이션**

  

### 표준 어노테이션

**@Override**

- 컴파일러에게 메서드를 오버라이딩하는 것이라고 알림.

**@Deprecated**

- 앞으로 사용하지 않을 대상임을 알림.

**@Functionallnterface**

- 함수형 인터페이스라는 것을 알림.

**@SuppressWarning**

- 컴파일러가 경고 메시지를 나타내지 않음.

**@SafeVaragrs**

- 제네릭과 같은 가변 인자의 매개변수를 사용할 때의 경고를 나타내지 않음.

  

### 메타 어노테이션

- 어노테이션에 붙이는 어노테이션으로, 어노테이션을 정의하는 데 사용함.

**@Target**

- 어노테이션을 정의할 때 적용 대상을 지정하는 데 사용함.

**@Documented**

- 어노테이션 정보를 javadoc으로 작성된 문서에 포함시킴.

**@Inherited**

- 어노테이션이 하위 클래스에 상속되도록 함.

**@Retention**

- 어노테이션이 유지되는 기간을 정하기 위해 사용함.

**@Repeatable**

- 어노테이션을 반복해서 적용할 수 있도록 함

  

### 사용자 정의 어노테이션

- 사용자가 직접 정의하여 사용하는 어노테이션임.

## 참고 자료

- https://ittrue.tistory.com/156