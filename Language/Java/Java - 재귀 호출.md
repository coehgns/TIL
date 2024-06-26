# 재귀 호출(recursive call)
- 재귀 호출이란 메소드 내부에서 **해당 메소드가 또다시 호출**되는 것을 의미합니다.
- 재귀 호출은 자기가 자신을 계속해서 호출하므로 끝없이 반복됩니다.
	- 메소드 내에 재귀 호출을 중단하도록 조건이 변경될 명령문을 반드시 포함해야 합니다.
- 재귀 호출은 알고리즘이나 자료 구조론에서 매우 중요한 개념입니다.

## 재귀 호출의 개념
```java
// 재귀 호출 X 예제

int sum(int n) {
	int result = 0;

	for(int i = 1; i <= n; i++) {
		result += i;
	}

	return result;
}
```
#### 위 코드는
- 목적을 바로 알 수 없습니다.
	- 코드를 해석해야 무슨 목적으로 만든 메소드인지 알 수 있습니다.
- 변수 i와 result는 왜 정의됐으며, for 문은 왜 사용되었는지 바로 알 수가 없습니다.

##### 1부터 4까지의 합을 구하는 알고리즘
1. 1부터 4까지의 합은 1부터 3까지의 합에 4를 더하면 됩니다.
2. 1부터 3까지의 합은 1부터 2까지의 합에 3를 더하면 됩니다.
3. 1부터 2까지의 합은 1부터 1까지의 합에 2를 더하면 됩니다.
4. 1부터 1까지의 합은 그냥 1입니다.

```java
// 재귀 알고리즘 O 예제

in recursiveSum(int n) {
	if(n == 1) {  // n이 1이면 그냥 1일 반환합니다.
		return 1;
	}
	return n + recursiveSum(n-1)  // n이 1이 아니면 n을 1부터 (n-1)까지의 합과 더한 값                                      을 반환합니다.
}
```
- if문이 존재하지 않으면 실행 직후 스택 오버플로우에 의해 종료될 것입니다.
	- if 문처럼 재귀 호출을 중단하기 위한 조건문을 반드시 포함해야 합니다.
		- 스택 오버플로우(stack overflow) : 메모리 구조 중 스택 영역에서 해당 프로그램이 사용할 수 있는 메모리 공간 이상을 사용하려고 할 때 발생합니다.

## 참고 자료
- https://www.tcpschool.com/java/java_usingMethod_recursive