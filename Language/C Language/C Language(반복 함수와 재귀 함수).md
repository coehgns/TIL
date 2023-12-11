## 반복 함수

- while 혹은 for 문법을 이용하여 특정한 처리를 반복하는 방식으로 문제를 해결하는 함수이다.

## 재귀 함수

- 자신의 함수 내부에서 자기 자신을 스스로 호출 함으로 써 재귀적으로 문제를 해결하는 함수이다.

------

### 숫자 피라미드

```c
#include <stdio.h>
int print(int a)
{
    int i, j;
    for (i = 0; i < a; i++)
    {
        for (j = 0; j <= i; j++)
        {
            printf("%d ", j + 1);
        }
        printf("\\n");
    }
    return 0;
}int main(void)
{
    int a;
    scanf("%d", &a);
    print(a);
    return 0;
}
```

<aside> ❓ 반복 함수 같은 경우는 오직 For 문과 while 문으로 구성된다.

</aside>

------

input : 10

- 출력 결과

1 1 2 1 2 3 1 2 3 4 1 2 3 4 5 1 2 3 4 5 6 1 2 3 4 5 6 7 1 2 3 4 5 6 7 8 1 2 3 4 5 6 7 8 9 1 2 3 4 5 6 7 8 9 10

------

### 특정한 문자열을 재귀 함수 반복 출력

```c
#include <stdio.h>
void print(int count)
{
    if (count == 0)
    {
        return;
    }
    else
    {
        printf("문자열을 출력합니다.\\\\n");
        print(count - 1);
    }
}
int main(void)
{
    int number;
    printf("문자열을 몇개 출력 할까요?\\n");
    scanf("%d", &number);
    print(number);
    return 0;
}
```

------

input : 10

- 출력 결과

문자열을 몇개 출력 할까요? 10 문자열을 출력합니다. 문자열을 출력합니다. 문자열을 출력합니다. 문자열을 출력합니다. 문자열을 출력합니다. 문자열을 출력합니다. 문자열을 출력합니다. 문자열을 출력합니다. 문자열을 출력합니다. 문자열을 출력합니다.

------

### 재귀 함수로 조합 구현

```c
#include <stdio.h>
int nCr(int n, int r)
{
	if (r == 0 || r == n)
	{
		return 1;
	}
	else
	{
		return nCr(n - 1, r - 1) + nCr(n - 1, r);
	}
}
int main(void)
{
	int n, r;
	scanf("%d %d", &n, &r);
	printf("%d", nCr(n, r));
	return 0;
}
```

------

input: 10 5

- 출력 결과

252