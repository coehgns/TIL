# 자료형

- char
- int
- double

## double

- double 이라는 **실수형**을 사용하여 연봉을 구할 수 있다.

```c
#include <stdio.h>
#define 달 12      //#define = 상수

int main(void)
{
	double 월급 = 100000.5;
	printf("%.2f 원", 월급 * 달);
	return 0;
}
```

## char and int

- 문자를 담기 위해 만들어진 변수형이지만, 그 실체는 정수형 변수이다.
- (아스키 코드) ex) A = 65 , B=66

```c
#include <stdio.h>
int main(void)
{
	int x = 'A';
	printf("%c\\n", x);
	char y = 65;
	printf("%c\\n", y);
	char z = 'B';
	printf("%d\\n", z);
	return 0;
}
```

## int changing

- int 형을 다른 진수로 바꿀 때
- 8진수는 %o (8진수:1 2 3 4 5 6 7 10 11 12 →)
- 16진수는 %x (16진수: 1 2 3 4 5 6 7 8 9 A B C D E→)

```c
#include <stdio.h>
int main(void)
{
	int x = 100;
	printf("10진수로 출력: %d\\n", x);
	printf("8진수로 출력 : %o\\n", x);
	printf("16진수로 출력: %x\\n", x);
	return 0;
}
```

### 참고 자료

- https://www.youtube.com/watch?v=9CKy2PL7s9w&list=PLRx0vPvlEmdDNHeulKC6JM25MmZVS_3nT&index=3

| 자료형 | 명칭      | 크키  |
| ------ | --------- | ----- |
|        | char      | 1byte |
|        | short     | 2byte |
| 정수형 | int       | 4byte |
|        | long      | 4byte |
|        | long long | 8byte |

| 자료형 | 명칭        | 크기       |
| ------ | ----------- | ---------- |
|        | float       | 4byte      |
| 실수형 | double      | 8byte      |
|        | long double | 8byte 이상 |