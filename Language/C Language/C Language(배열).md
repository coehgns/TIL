## 배열

- 데이터가 많을 때 주로 배열을 이용한다.

### 5개의 정수 중에서 최댓값과 최솟값의 위치를 출력하는 프로그램

------

```c
#include <stdio.h>
#include <limits.h>
#define NUMBER 5
int main(void)
{
	int i, max, min, index;
	int array[NUMBER];
	max = 0;
	index = 0;
	// array[0]~array[4] : 총 5개가 들어갈 수 있는 크기의 배열 선언
	for (i = 0; i < NUMBER; i++)
	{
		scanf("%d", &array[i]);
		if (max < array[i])
		{
			max = array[i];
			index = i;
		}
	}
	printf("가장 큰값은 %d 입니다. 그리고 %d 번 째에 있습니다.\\n", max, index, index + 1);
	min = INT_MAX;
	for (i = 0; i < NUMBER; i++)
	{
		scanf("%d", &array[i]);
		if (min > array[i])
		{
			min = array[i];
			index = i;
		}
	}
	printf("가장 작은은 %d 입니다. 그리고 %d 번 째에 있습니다.\\n", min, index, index + 1);
	return 0;
}
```

input: 30 33 90 35 70

- 출력 결과

가장 큰값은 90 입니다. 그리고 2 번 째에 있습니다. 가장 작은은 30 입니다. 그리고 0 번 째에 있습니다.

------

### 5개의 정수 중에서 짝수 최댓값과 홀수 최댓값을 구하는 프로그램

```c
#include <stdio.h>
#define NUMBER 5
int main(void)
{
	int array[NUMBER];
	int i, oddMAX, evenMAX;
	oddMAX = 0;
	evenMAX = 0;
	for (i = 0; i < NUMBER; i++)
	{
		scanf("%d", &array[i]);
		if (array[i] % 2 == 0)
		{
			if (evenMAX < array[i])
			{
				evenMAX = array[i];
			}
		}
		else
		{
			if (oddMAX < array[i])
			{
				oddMAX = array[i];
			}
		}
	}
	printf("%d %d", oddMAX, evenMAX);
	return 0;
}
```

------

input : 15 450 200 405 600

출력 결과

405 600