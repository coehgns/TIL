# 조건문과 반복문

## 조건문

```c
#include <stdio.h>

int main(void)
{
	int x = -150;
	if (x < 0)
	{
		x = -x;
	}
	printf("x의 절댓값은 %d입니다.\\n", x);
	return 0;
}
```

<aside> ❓ 만약 x가 0보다 작다면 x가  -x로 출력 된다는 뜻이다.

</aside>

------

- 출력 결과

x의 절댓값은 150입니다.

```c
#include <stdio.h>

int main(void)
{
	int score = 85;   //학생의 점수를 의미한다.                  
	if (score >= 90)
	{
		printf("당신의 학점은 A입니다.\\n");
	}
	else if (score >= 80)
	{
		printf("당신의 학점은 B입니다.\\n");
	}
	else if (score >= 70)
	{
		printf("당신의 학점은 C입니다.\\n");
	}
	else if (score >= 60)
	{
		printf("당신의 학점은 D입니다.\\n");
	}
	else
	{
		printf("당신의 학점은 F입니다.");
	}
	return 0;
}
```

<aside> ❓ else if 문장과 else 문장은 if 문장이 존재 할 때만 사용 가능하다.

</aside>

------

- 출력 결과

당신의 학점은 B입니다.

## 윤년 판독 프로그램

```c
#include <stdio.h>

int main(void)
{
	/* 윤년 => 4년마다, 그렇지만 100년 단위 일 때는 윤년에 해당하지 않도록
	윤년 => 400년 단위 일 때는 어떤 상황이든간에 윤년으로 설정한다고.*/
	int year = 2016;
	if ((year % 4 == 0 && year % 100 != 0) || year % 400 == 0)
	{
		printf("%d년은 윤년입니다.\\n", year);
	}
	else
	{
		printf("%d년은 윤년이 아닙니다.\\n", year);
	}
	return 0;
}
```

------

- 출력 결과

2016년은 윤년입니다.

## 반복문

```c
#include <stdio.h>

int main(void)
{
	int i = 1, sum = 0;
	while (i <= 1000)
	{
		sum = sum + i;
		i++;
	}
	printf("1부터 1000까지의 합은 %d입니다.\\n", sum);
	return 0;

}
```

<aside> ❓ while() 이라는 반복문을 사용하여 변수 sum에 1을 계속 더하여 1000까지의 합을 출력 할 수 있다.

</aside>

------

- 출력 결과

1부터 1000까지의 합은 500500입니다.

## 사각형 출력

```c
#include <stdio.h>
#define N 10

int main(void)
{
        int i, j;
        for (i = 0; i < N; i++)
        {
                       for (j = 0; j < N; j++)
                       {
                                printf("★");
                       }
                       printf("\\n");
        }
return 0;
}
```

<aside> ❓ for()이라는 반복문을 사용하여 상수 N인 10 까지 i와 j에 횟수를 1씩 더하여 ★을 출력한다. 그 과정에서 줄 바꿈을 통해 사각형을 만들 수 있다.

</aside>

------

- 출력 결과

★★★★★★★★★★ ★★★★★★★★★★ ★★★★★★★★★★ ★★★★★★★★★★ ★★★★★★★★★★ ★★★★★★★★★★ ★★★★★★★★★★ ★★★★★★★★★★ ★★★★★★★★★★ ★★★★★★★★★★

## 피라미드 출력

```c
#include <stdio.h>
#define N 20

int main(void)
{
    int i, j;
    for (i = 0; i < N; i++)
    {
        for (j = N - i - 1; j > 0; j--)
        {
            printf("   ");
        }
        for (j = 0; j < i; j++)
        {
            printf("★ ");
        }
        for (j = 0; j < i - 1; j++)
        {
            printf("★ ");
        }
        printf("\\n");
    }
    return 0;
}
```

<aside> ❓ i가 상수 N인 20번 반복된다.

</aside>

for (j = N - i - 1; j > 0; j--) { printf("   ");                      ← j가 0보다 클 때 까지 1씩 감소시켜 공백을 }                                                    넣는다.

j>0 이 부분이 참이면 무한정 반복이 가능하다.

------

- 출력 결과

  ![스크린샷(2)](C:\Users\컴퓨터\Pictures\Screenshots\스크린샷(2).png)