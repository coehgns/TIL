# 동적 메모리

## 동적 메모리

- 동적 메모리는 마치 수납 공간에서 물건을 꺼내는 것과 비슷하다. 동적 메모리의 사용이 끝나면 반드시 해당 메모리 영역을 명시적으로 반납을 해주어야 한다.

### 동적 메모리 기초 예제

```c
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    int *pi; // Pointer Integer
    pi = (int *)malloc(sizeof(int)); //malloc = 메모리를 할당해라.
    if(pi ==NULL)
    {
        printf("동적 메모리 할당에 실패했습니다.\\n");
        exit(1);
    }
    *pi = 100;
    printf("%d\\n", *pi);
    /* 동적 메모리 사용한 이후에는 무조건 해당 메모리를 반환합니다. */
    free(pi);
    
    return 0;
}
```

------

- 출력 결과

100

------

### 동적 메모리로 알파벳 출력 하기

```c
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    char *pc = NULL;
    int i = 0;
    pc =(char *)malloc(100 * sizeof(char));
    if(pc == NULL)
    {
        printf("동적 메모리 할당에 실패했습니다.\\n");
        exit(1);
    }
    /* pc가 가르키는 포인터를 1씩 증가시키며 알파벳 소문자를 삽입합니다. */
    for(i = 0; i < 26; i++)
    {
        *(pc + i) = 'a' + i;
    }
    /* 아스키 코드에서 0은 NULL을 의미한다. */
    *(pc + i) = 0;
    
    printf("%s\\n", pc);
    free(pc);
    return 0;
}
```

------

- 출력 결과

abcdefghijklmnopqrstuvwxyz

------

### 동적 메모리로 정수 5개를 처리하기

```c
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    int *pi, i;
    pi = (int *)malloc(5 * sizeof(int));
    if(pi == NULL)
    {
        printf("동적 메모리 할당에 실패했습니다.\\n");
        exit(1);
    }
    pi[0] = 100;
    pi[1] = 200;
    pi[2] = 300;
    pi[3] = 400;
    pi[4] = 500;
    for(i = 0; i< 5; i++)
    {
        printf("%d\\n", *(pi + i));
    
    }
    free(pi);
    return 0;
}
```

------

- 출력 결과

100 200 300 400 500