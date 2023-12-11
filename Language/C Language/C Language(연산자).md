# 연산자 (계산의 기본)

## 나누기, 모듈러 연산

```c
#include <stdio.h>
#define SECOND_PER_MINIUTE 60

int main(void)
{
	int input = 1000;
	int miniute = input / SECOND_PER_MINIUTE;  //← / (나누기 연산자)
		int second = input % SECOND_PER_MINIUTE;   //← % (모듈러 연산자)
		printf("%d초 %d분 %d초 입니다.\\n", input, miniute, second);
	return 0;
}
```

- 출력 결과

1000초 16분 40초입니다.

## 증감연산자

```c
#include <stdio.h>

int main(void)
{
	int x = 0;
	printf("현재의 x의 값은 %d입니다. \\n", x);     //← x++(증감연산자)
	x++;
	printf("현재의 x의 값은 %d입니다. \\n", x);
	printf("현재의 x의 값은 %d입니다. \\n", x--);   //←  x- - (증감연산자)
	printf("현재의 x의 값은 %d입니다. \\n", x);
	printf("현재의 x의 값은 %d입니다. \\n", --x);    //← - -x(증감연산자)
	return 0;
}
```

- 출력 결과

현재의 x의 값은 0입니다. 현재의 x의 값은 1입니다. 현재의 x의 값은 1입니다. 현재의 x의 값은 0입니다. 현재의 x의 값은 -1입니다.

## 복합 대입 연산자

```c
#include <stdio.h>

int main(void)
{
	int x = 100;
	printf("현재 x의 값은 %d입니다. \\n", x);
	x += 50;  // x = x+50                           // ←x = x+50
	printf("현재 x의 값은 %d입니다.\\n", x);
	x -= 50;                                                // ←x = x-50
	printf("현재 x의 값은 %d입니다.\\n", x);
	x *= 50;                                               // ← x = x x* 50
	printf("현재 x의 값은 %d입니다. \\n", x);
	x /= 50;                                               // ←x = x 나누기 50
	printf("현재 x의 값은 %d입니다. \\n", x);
	x %= 3;                                             // ← x = x % 3
	printf("현재 x의 값은 %d입니다. \\n", x);
	return 0;
}
```

- 출력 결과

현재 x의 값은 100입니다. 현재 x의 값은 150입니다. 현재 x의 값은 100입니다. 현재 x의 값은 5000입니다. 현재 x의 값은 100입니다. 현재 x의 값은 1입니다.

## 관계 연산자

```c
#include <stdio.h>

int main(void)
{
	int x = 50, y = 30;
	printf("x가 y와 같은가? %d\\n", x == y);
	printf("x가 y와 다른가? %d\\n", x != y);
	printf("x가 y보다 큰가? %d\\n", x > y);
	printf("x가 y보다 작은가?%d\\n", x < y);
	printf("x에 y값을 넣으면? %d\\n", x = y);
	return 0;
}
```

- 출력 결과

x가 y와 같은가? 0   (← 거짓의 뜻으로 0이 출력이 됨.) x가 y와 다른가? 1   (← 참의 뜻으로 1이 출력이 됨.) x가 y보다 큰가? 1 x가 y보다 작은가?0 x에 y값을 넣으면? 30

## 논리 연산자

```c
#include <stdio.h>

int main(void)
{
	int x = 50, y = 30;
	printf("x가 y보다 크고 40미만 입니까?%d\\n", (x > y) && (y < 40));
	printf("x가 y보다 작거나 y가 30입니까?%d\\n", (x < y) || (y == 30));
	printf("x가 50이 아닙니까?%d\\n", (x != 50));
	return 0;
}
```

- 출력 결과

x가 y보다 크고 40미만 입니까?1 x가 y보다 작거나 y가 30입니까?1 x가 50입니까?0

## 비교 연산자

| 종류        | 기호      | 문법         | 의미                             |
| ----------- | --------- | ------------ | -------------------------------- |
|             | ==        | a==3         | a와 3이 같은가?                  |
|             | ! =       | a! = 3       | a와 3이 다른가?                  |
| 비교 연산자 | >, <      | a>3,a<3      | a가 3보다 큰(작은)가?            |
|             | > = , < = | a> = , < = 3 | a가 3보다 크거나(작거)나 같은가? |

## 논리 연산자

| 종류        | 기호 | 문법 | 의미                          |
| ----------- | ---- | ---- | ----------------------------- |
|             | &&   | a&&b | a와 b가 모두 참일 경우에만 참 |
| 논리 연산자 |      |      |                               |
|             | !    | !a   | a가 참이면 거짓, 거짓이면 참  |

## 조건 연산자

```c
#include <stdio.h>

int main(void)
{
	int x = -50, y = 30;
	int absoluteX = (x > 0) ? x : -x;  //(참이면 x가 출력되고, 거짓이면 -x가 출력된다.)
	int max = (x > y) ? x : y;    // (참이면 x가 출력되고, 거짓이면 y가 출력된다.)
	int min = (x < y) ? x : y;
	printf("x의 절댓값은 %d입니다.\\n", absoluteX);
	printf("x와 y중에서 최댓값은 %d입니다.\\n", max);
	printf("x와 y중에서 최솟값은 %d입니다.\\n", min);
	return 0;
}
```

------

- 출력 결과

x의 절댓값은 50입니다. x와 y중에서 최댓값은 30입니다. x와 y중에서 최솟값은 -50입니다.

------

## pow()  거듭제곱 연산 함수

```c
#include <stdio.h>
#include <math.h> //pow() abs()

int main(void)
{
	double x = pow(2.0, 20.0);
	printf("2의 20 제곱은 %.0f입니다.\\n", x);
	return 0;
}
```

------

- 출력 결과

2의 20제곱은 1048576입니다.