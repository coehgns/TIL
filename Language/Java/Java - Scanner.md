# Java - Scanner

# Scanner

- `Scanner` 클래스를 사용하면 사용자 입력을 매우 편리하게 받을 수 있습니다.

**Scanner1**

```java
package scanner;

import java.util.Scanner;

public class Scanner1 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("문자열을 입력하세요:");
        String str = scanner.nextLine(); // 입력을 String으로 가져온다.
        System.out.println("입력한 문자열: " + str);

        System.out.print("정수를 입력하세요: ");
        int intValue = scanner.nextInt();
        System.out.println("입력한 정수: " + intValue);

        System.out.print("실수를 입력하세요: ");
        double doubleValue = scanner.nextDouble();
        System.out.println("입력한 실수: " + doubleValue);
    }
}
```

- ```
  Scanner scanner = new Scanner(System.in);
  ```

  - `Scanner` 의 기능을 사용하기 위해 `new` 를 사용해서 `Scanner`를 만듭니다.
  - `Scanner`는 `System.in`을 사용해서 사용자의 입력을 편리하게 받도록 도와줍니다.
  - `Scanner scanner` 코드는  `scanner` 변수를 선언하는 것 입니다.
  - 선언 후 `scanner` 변수를 통해서 `scanner`를 사용할 수 있습니다.

- ```
  scanner.nextLine()
  ```

  - 엔터(\n)를 입력할 때 까지 문자를 가져옵니다.

- ```
  scanner.nextInt()
  ```

  - 입력을 `int`형으로 가져옵니다.
  - 정수 입력에 사용합니다.

- ```
  scanner.nextDouble()
  ```

  - 입력을 `double`형으로 가져옵니다.
  - 실수 입력에 사용합니다.

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194594