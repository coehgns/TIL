# 사용자 정의 함수

- 정해진 특정한 기능을 수행하는 모듈을 의미
- 함수는 각각의 모듈로서 쉽게 수정되고 보완될 수 있다는 장점이 있다.

### 시간 더하기 프로그램

```c
#include <stdio.h>

// 전역 함수
int hour;
int miniute;
int miniuteAdd;

void counter()
{
	miniute += miniuteAdd;
	hour += miniute / 60;
	miniute % 60;
	hour %= 24;
}
int main(void)
{
	printf("시를 입력하세요:");
	scanf("%d", &hour);
	printf("분을 입력하세요:");
	scanf("%d", &miniute);
	printf("더할 분을 입력하세요:");
	scanf("%d", &miniuteAdd);
	counter();
	printf("더해진 시간은 %d시 %d분 입니다.\\n", hour, miniute);
	return 0;
}
```

------

- 출력 결과

시를 입력하세요:12

분을 입력하세요: 30

더할 분을 입력하세요: 40

더해진 시간은 13시 10분 입니다.

------

### 화폐의 개수는 최소한으로 주는 방법 프로그램

```c
#include <stdio.h>

int smallest(int number)
{
	int count = 0;
	while (number >= 50000)
	{
		number -= 50000;
		count++;
	}
	while (number >= 10000)
	{
		number -= 10000;
		count++;
	}
	while (number >= 5000)
	{
		number -= 5000;
		count++;
	}
	while (number >= 1000)
	{
		number -= 1000;
		count++;
	}
	while (number >= 500)
	{
		number -= 500;
		count++;
	}
	while (number >= 100)
	{
		number -= 100;
		count++;
	}
	while (number >= 50)
	{
		number -= 50;
		count++;
	}
	while (number >= 10)
	{
		number -= 10;
		count++;
	}
	return count;
}

int main(void)
{
	int number;
	printf("금액을 입력하세요:");
	scanf("%d", &number);
	printf("최소로 줄 수 있는 화폐의 개수는 %d개 입니다.\\n", smallest(number));
	return 0;
}
```

------

- 출력 결과

금액을 입력하세요: 3700

최소로 줄 수 있는 화폐의 개수는 6개 입니다.

```
                           (1000원 3개,500원 1개,100원 2개)
```

------

### 1월 1일 부터 현재 까지의 날짜 차이 구하는 프로그램

```c
#include <stdio.h>

int getDays(int month, int day)
{
	int i, sum = 0;
	for (i = 1; i < month; i++)
	{
		if (i == 2)
		{
			sum += 28;
		}
		else if (i % 2 == 0)
		{
			sum += 30;
		}
		else
		{
			sum += 31;
		}
	}
	retun sum + day;
}

int main(void)
{
	int month, day;
	scanf("%d %d", &month, &day);
	printf("1월 1일 부터 해당 날짜 까지의 거리는 %d일 입니다.", gteDays(month, day));
	return 0;
}
```

------

- 출력 결과

11 11

1월 1일 부터 해당 날짜 까지의 거리는  314일 입니다.