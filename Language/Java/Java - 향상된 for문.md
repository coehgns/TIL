# 향상된 for문
- 각각의 요소를 탐색한다는 의미로 for-each문이라고도 많이 부릅니다.
- 향상된 `for문`은 배열을 사용할 때 기존 `for문` 보다 더 편리하게 사용할 수 있습니다.
- 일반 for문과 동일하게 작동합니다.
- 향상된 for문은 배열의 인덱스를 사용하지 않고, 종료 조건을 주지 않아도 됩니다.
- 단순히 해당 배열을 처음부터 끝까지 탐색합니다.
- 향상된 for문은 배열의 인덱스를 사용하지 않고도 배열의 요소를 순회할 수 있기 때문에 코드가 간결하고 가독성이 좋습니다.
## 향상된 for문 정의
```java
for (변수 : 배열 또는 컬렉션) {
   // 배열 또는 컬렉션의 요소를 순회하면서 수행할 작업
}
```
```java
package array;  
  
public class EnhancedFor1 {  
    public static void main(String[] args) {  
        int[] numbers = {1, 2, 3, 4, 5};  
  
        // 일반 for문  
        for(int i = 0; i < numbers.length; i++) {  
            int number = numbers[i];  
            System.out.print(number + " ");  
        }  
        System.out.println();  
  
        // 향상된 for문  
        for(int number : numbers) {  
            System.out.print(number + " ");  
        }  
    }  
}    
// 출력
// 1 2 3 4 5
// 1 2 3 4 5
```
## 참고 자료
- https://www.inflearn.com/course/lecture?courseSlug=%EA%B9%80%EC%98%81%ED%95%9C%EC%9D%98-%EC%9E%90%EB%B0%94-%EC%9E%85%EB%AC%B8&unitId=194610