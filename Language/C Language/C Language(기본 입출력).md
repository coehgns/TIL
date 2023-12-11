# 기본 입출력

- C언어에서 기본 입출력 함수를 이용하여 사용자와 상호작용을 할 수 있다.
- 사용자로부터 입력 받을 자료형에 따라서 %d, %c, %f, %lf 등의 다양한 문법을 사용해야 한다는 것에 유의 해야 한다.

## 계산기 프로그램

```c
#include<stdio.h>
int main(void)
{
	char o;
	int x, y;
	while (1)
	{
		printf("수식을 입력하세요 : ");
		scanf("%d %c %d", &x, &o, &y);
		if (o == '+')
		{
			printf("%d %c %d = %d\\n", x, o, y, x + y);
		}
		else if (o == '-')
		{
			printf("%d %c %d = %d\\n", x, o, y, x - y);
		}
		else if (o == '*')
		{
			printf("%d %c %d = %d\\n", x, o, y, x * y);
		}
		else if (o == '/')
		{
			printf("%d %c %d = %d\\n", x, o, y, x / y);
		}
		else if (o == '%')
		{
			printf("%d %c %d = %d\\n", x, o, y, x % y);
		}
		else
		{
			printf("입력이 잘못 되었습니다.\\n");
		}

		return 0;

	}
```

------

- 출력 결과

수식을 입력하세요 : 8*2

8*2=16

------

## 구구단 프로그램

```c
#include <stdio.h>

int main(void)
{
	int x, i;
	printf("정수를 입력하세요:");
	scanf("%d", &x);
	for (i = 1; i <= 9; i++);
	{
		printf("%d X %d =%d\\n", x, i, x * i);
	}
	return 0;

}
```

------

- 출력 결과

정수를 입력하세요 : 3

3 x 1 =3

3 x 2 =6

3 x 3 =9

3 x 4 =12

3 x 5 =15

3 x 6 =18

3 x 7 =21

3 x 8 =24

3 x 9 =27