# 문자열

char array[10];    → 영어 10글자, 한글 5글자

영어:1개 크기(1byte)

한글:2개 크기(2byte)

## 하나의 문자열 안의 글자수 세기

```c
#include <stdio.h>

int main(void)
{
    char input[1001];
    gets(input);
    int count =0;
    while(input[count] != '\\0')
    {
        count++;
    }
    printf("입력한 문자열의 길이는 %d입니다.\\n",count);
    printf("입력한 문자열:%s",input);
    return 0;
}
```

------

input: hello

- 출력 결과

입력한 문자열의 길이는 5입니다.

입력한 문자열: hello

------

### strlen()

```c
#include <stdio.h>
#include <string.h>

int main(void)
{
    char input[5]="Love";
    printf("문자열의 길이: %d\\n",strlen(input));
    return 0;
}
```

------

- 출력 결과

문자열의 길이:4

------

### strcmp()

```c
#include <stdio.h>
#include <string.h>

int main(void)
{
    char inputOne[5]="A";
    char inputTwo[5]="B";
    printf("문자열의 비교: %d\\n", strcmp(inputOne, inputTwo));
    return 0;
}
```

------

- 출력 결과

문자열의 비교:-1 ( A ,B 두 문자가 사전적으로 동일하면 0, inputOne이 앞에 있으면 -1, 그렇지 않으면 1이 출력 된다.

------

### strcpy()

```c
#include <stdio.h>
#include <string.h>

int main(void)
{
    char input[10] = "GFD";
    char result[5] = "Love";
    strcpy(result, input);
    printf("문자열 복사 : %s\\n", result);
    return 0;
}
```

------

- 출력 결과

문자열 복사 : GFD