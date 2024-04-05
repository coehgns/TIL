# 2차원 배열
- 2차원 배열은 행과 열로 구성됩니다.
## 2차원 배열 선언
```java
int[][] arr = new int[2][3];

or

int[][] arr = new int[][] {
    {1, 2, 3},
    {4, 5, 6}
};

arr[행][열] arr[row][column]
```
## 2차원 배열 예제
```java
package array;  
  
public class ArrayDi2 {  
  
    public static void main(String[] args) {  
        // 2x3 2차원 배열  
        int[][] arr = new int[][] {
		    {1, 2, 3},
		    {4, 5, 6}
		};  // 2행 3열  
    
  
        for(int row = 0; row < arr.length; row++) {  
            for(int col = 0; col < arr[row].length; col++) {  
                System.out.print(arr[row][col] + " ");  
            }  
            System.out.println();  
        }  
    }  
}
```

```java
package array;  
  
public class ArrayDi3 {  
  
    public static void main(String[] args) {  
        // 2x3 2차원 배열  
        int[][] arr = new int[3][3];  // 2행 3열  
  
        int i = 1;  
        for(int row = 0; row < arr.length; row++) {  
            for(int col = 0; col < arr[row].length; col++) {  
                arr[row][col] = i++;  
            }  
        }  
  
        for(int row = 0; row < arr.length; row++) {  
            for(int col = 0; col < arr[row].length; col++) {  
                System.out.print(arr[row][col] + " ");  
            }  
            System.out.println();  
        }  
    }  
}
```
## 참고 자료
- https://www.inflearn.com/course/lecture?courseSlug=%EA%B9%80%EC%98%81%ED%95%9C%EC%9D%98-%EC%9E%90%EB%B0%94-%EC%9E%85%EB%AC%B8&unitId=194609
- https://www.inflearn.com/course/lecture?courseSlug=%EA%B9%80%EC%98%81%ED%95%9C%EC%9D%98-%EC%9E%90%EB%B0%94-%EC%9E%85%EB%AC%B8&unitId=194608
- https://www.inflearn.com/course/lecture?courseSlug=%EA%B9%80%EC%98%81%ED%95%9C%EC%9D%98-%EC%9E%90%EB%B0%94-%EC%9E%85%EB%AC%B8&unitId=194607