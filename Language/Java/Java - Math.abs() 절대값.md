# Math.abs()
- Math.abs() 메소드를 사용하여 int, long, double, float 타입 숫자의 절대값을 구할 수 있습니다.
-  java.lang.Math 클래스는 수학 연산에 필요한 다양한 메소드들을 제공합니다.
## 
```java
import java.util.Scanner;  
  
public class Main {  
  
    public static void main(String[] args) {  
        Scanner input = new Scanner(System.in);  
  
        long n = input.nextLong();  
        long m = input.nextLong();  
  
        long sum = n - m;  
  
        System.out.println(Math.abs(sum));  
    }  
}

// input : -2 5
// output : 7
```
## 참고 자료
- https://hianna.tistory.com/525