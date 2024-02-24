# Java - 주석문

# 주석

- 주석문이란 프로그램의 코드와 실행에 영향을 주지 않는 문장.
- 코드를 설명할 때 또는 예시를 들 때 주로 사용함.

## 주석 사용

- 행 단위 주석인 // 와  블럭단위 주석인 /* ~ */ 가 사용됨.

```java
package first;

public class HelloWorld {
// 주석
	public static void main(String[] args) {
		System.out.println("Hello World");
		System.out.println("test");
/*		System.out.println("1");
		System.out.println("2");
		System.out.println("3"); */

	}

}
```

# 문서화 주석

- /** 를 사용하여 코드의 내용을 더 자세히 설명 가능함.

```java
package first;

public class HelloWorld {
// 주석
	/**                         
	 * 
	 * @param args
	 */
	public static void main(String[] args) {
		System.out.println("Hello World");
		System.out.println("test");
/*		System.out.println("1");
		System.out.println("2");
		System.out.println("3"); */

	}

}
```

### 주석 단축키

- Ctrl + /

## 참고 자료

- https://school.programmers.co.kr/learn/courses/5/lessons/108