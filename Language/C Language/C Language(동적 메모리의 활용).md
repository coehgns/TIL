# 동적 메모리의 활용

### 구조체 동적 메모리 할당

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct Book
{
  int number;
  char title[100];
};

void showBook(struct  Book *p, int n)
{
    int i;
    for(i = 0; i < n; i++)
    {
        printf("번호 %d : %s\\n", (p + i)->number, (p + i)->title);
    }
}

int main(void)
{
    struct Book *p;
    p = (struct Book *)malloc(2 * sizeof(struct Book));
    if(p == NULL)
    {
        printf("동적 메모리 할당에 실패했습니다.\\n");
        exit(1);
    }
    
    p->number = 1;
    strcpy(p->title, "C Programming");
    
    (p + 1)->number = 2;
    strcpy((p + 1)-> title, "Data Structure");
    
    showBook(p,2);
    free(p);
    return 0;
}
```

------

- 출력 결과

번호 1 : C Programming 번호 2 : Data Structure

------

### 동적 메모리 2차원 배열

```c
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    int i, x, y;
    int** pptr = (int**)malloc(sizeof(int*) * 8);
    for(i = 0; i < 8; i++)
    {
        *(pptr + i) = (int * )malloc(sizeof(int) * 6);
    }
    
    for(y =0; y < 8; y++)
    {
        for(x = 0; x < 6; x++)
        {
            *(*(pptr + y) + x) = 6 * y + x;
        }
    }
    
    for(y = 0; y < 8; y++)
    {
        for(x = 0; x < 6; x++)
        {
            printf("%3d", *(*(pptr + y) + x));
        }
        printf("\\n");
    }
    
    for(y = 0; y < 8; y++)
    {
        free(*(pptr + y));
    }
    return 0;
}
```

------

- 출력 결과

0  1  2  3  4  5 6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47