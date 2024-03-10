# Java - AssertJ

# AssertJ

- 자바 JUnit의 테스트 코드에 사용되어, 테스트 코드의 **가독성**과 **편의성**을 높여 주는 라이브러리입니다.
- 메서드 체이닝을 지원해, 더 직관적이고 읽기 쉬운 테스트 코드 작성이 가능합니다.
- 테스트에 필요한 풍부한 메소드들을 제공합니다.
- 자바 8 이상은 AssertJ 3.x 버전을 사용해야 합니다.

```java
// 자바 8 기준, Gradle 사용

testCompile 'org.assertj:assertj-core:3.6.2'
```

## AssertJ 메소드 임포트

```
import static org.assertj.core.api.Assertions.*;
import org.junit.jupiter.api.Test;
```

- static 임포트를 통해 AssertJ의 다양한 API를 클래스 이름 없이 사용 가능합니다.

## AssertJ assert 메소드

- AssertJ에서 모든 테스트 코드는 `aasertThat()`으로 시작합니다.
- `assertThat (테스트 타겟) .메소드1() .메소드2() .메소드3()``
  - 이런 포맷으로 AssertJ의 여러 메소드들을 연쇄적으로 호출해 코드를 작성할 수 있습니다.

### 예제 - 문자열 테스트

```
isNotEmpty()`, `contains(e)`, `doesNotContain(e)`, `startsWith(e)`, `endsWith(e)`, `isEqualTo(e)
asserThat("Hello, world! Nice to meet you.") // 주어진 "Hello, world! Nice to meet you."라는 문자열은
                .isNotEmpty() // 비어있지 않고
                .contains("Nice") // "Nice"를 포함하고
                .contains("world") // "world"도 포함하고
                .doesNotContain("ZZZ") // "ZZZ"는 포함하지 않으며
                .startWith("Hell") // "Hell"로 시작하고
                .endsWith("u.") // "u. "로 끝나며
                .isEqualTo("Hello, world! Nice to meet you."); // "Hello, world! Nice to meet you."와 일치합니다.
```

### 예제 - 숫자 테스트

```java
asserThat(3.14d) // 주어진 3.14라는 숫자는 
              .isPositive() // 양수이고
              .isGreaterThan(3) // 3보다 크며
              .isLessThan(4) // 4보다 작습니다
              .isEqualTo(3, offset(1d)) // 오프셋 1 기준으로 3과 같고
              .isEqualTo(3.1, offset(0.1d)) // 오프셋 0.1 기준으로 3.1과 같으며
              .isEqualTo(3.14); // 오프셋 없이는 3.14와 같습니다
```

## AsserJ의 메서드들

### 일반

**Assert 인터페이스**

- 모든 Assertion 객체가 기본적으로 제공합니다.

- `isEqualTo(Object o)` : 실제 값이 주어진 값과 같은지 확인합니다.

  ```
  `isNotEqualTo(Object o)` : 실제 값이 주어진 값과 다른지 확인합니다.
  ```

- `isInstanceOf(Class<?> type)`, `isInstanceOfAny(Class<?> ...types)`

  - : 실제 값이 주어진 클래스 유형이 아닌지 확인합니다.
  - `isNotInstanceOf(Class<?> type)`, `isNotInstanceOfAny(Class<?> ... types)` 는 그 반대입니다.

- `isExactlySamInstanceOf(Class<?> type)` : 실제 값이 정확히 주어지 유형의 인스턴스인지 확인합니다.

  - `isNotExactlyInstanceOf(Class<?> type)` 는 그 반대입니다.

- `asList()` : 실제 값이 List의 인스턴스인지 확인하고 list Assertion을 반환합니다.

- `asString()` : toString()으로 실제 값에 대한 문자열을 반환합니다.

- `hasSameClassAs(Object o)`, `doesNotHaveSameClassAs(Object o) hasSameHashCodeAs(Object o)`, `doesNotHaveSameHashCodeAs(Object o)`

  - 실제 값 / 객체가 주어진 객체와 동일한 클래스 / 해시 코드를 가지고 있는지 확인합니다.
  - `doesNot`이 붙은 메소드는 반대로, 가지고 있지 않은지를 확인합니다.

- `hasToString(String str)`, `doesNotHaveToString(String str)` : 실제 `actual.toString() 값이 주어진 String과 같은지 확인합니다. `doesNot` 이 붙은 메소드는 반대로, 같지 않은지 확인합니다.

- `isIn(Iterable<?> v)`, `isIn(Object ... v)` : 주어진 iterable 또는 값 배열에 실제 값이 있는지 확인합니다. `isNotIn(iterable<?> v)` , `isNotIn(Object ... v)` 는 그 반대입니다.

- `isNull()` : 실제 값이 null인지 확인합니다. `isNotNull()`은 그 반대입니다.

- `isSameAs(Object o)` : `==` 비교를 사용해 실제 값이 주어진 값과 동일한지 확인합니다. `isNotSameAs(Object o)`는 그 반대입니다.

- `as("설명")` : Assertion을 설명하는 메서드입니다. ”설명”의 내용이 테스트 결과에 출력되도록 할 수 있습니다.

### 숫자 관련 메서드

- `isBetween(start, end)` : 실제 값이 start에서 end 값 사이에 있는지 확인합니다. (start, end 값을 포함합니다.)
- `isStrictlyBetween(Start, end)` : 실제 값이 start에서 end 값 사이에 있는지 확인합니다. (start, end 값을 포함하지 않습니다.)
- `isCloseTo(expected, offset)`, `isCloseTo(expected, percentage)` : 실제 숫자가 주어진 offset / percentage 내에서 expected에 가까운지 확인합니다. 차이가 offset / percentage와 같으면 Assertion은 유효한 것으로 간주합니다.
- `isNotCloseTo(expected, offset)`, `isNotCloseTo(expected, percentage)` : 실제 숫자가 주어진 offset / percentage 내에서 expected에 가깝지 않은지 확인합니다. 차이가 offset / percentage와 같으면 Assertion은 실패한 것으로 간주합니다.
- `isPositive()` , `isNegative()` : 실제 값이 양수인지 / 음수인지 확인합니다.
- `isNotPositive()`, `isNotNegative()` : 실제 값이 양수가 아닌지 (음수이거나 0인지) / 음수가 아닌지 (양수이거나 0인지) 확인합니다.
- `isZero()` : 실제 값이 0인지 확인합니다. `isNotZero()`: 실제 값이 0이 아닌지 확인합니다.
- `isOne()` : 실제 값이 1과 같은지 확인합니다.

### 부동소수점 숫자 관련 메서드

- `isNaN()` : 실제 값이 NaN과 같은지 확인합니다. `isNotNaN()` : 실제 값이 NaN과 같지 않은지 확인합니다.
- `isFinite()` , `isinfinite()`

### Assertj 사용시 주의점

- `assertThat(Object o)`로 테스트할 객체를 호출한 다음 메서드들을 사용해야 합니다.

  - BAD : `assertThat(actual.equals(expected));`
     GOOD : `assertThat(actual).isEqualsTo(expected);`
  - BAD : `asertThat(1==2);` GOOD : `assertThat(1).isEqualsTo(2);`

- `as()` 는 assertion 메소드들을 호출하기 전에 사용해야 합니다.

  - BAD

  ```java
  // DON'T DO THIS ! as/descr ibedAs have no effect after the assertion
  assertThat(actual).isEqualTo(expected).as("description");
  assertThat(actual).isEqualTo(expected).describedAs("description");
  ```

  - GOOD

  ```java
  // DO THIS: use as/descr ibedAs before the assertion
  assertThat(actual).as("description").isEqualsTo(expected);
  assertThat(actual).describedAs("description").isEqualsTo(expected);
  ```

## 참고 자료

- https://bibi6666667.tistory.com/231