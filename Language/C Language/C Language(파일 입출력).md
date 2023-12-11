# 파일 입출력

```c
#include <stdio.h>
 
int main(void)
{
    FILE *fp = NULL;
    fp = fopen("output.txt","w");
    //w -> 쓰기 모드 (Write), r -> 읽기 모드 (Read)
    if(fp == NULL)
    {
        printf("파일 열기에 실패했습니다.\\n");
    }
    else 
    {
        printf("파일 열기에 성공했습니다.\\n");
    }
    fputc('H', fp);
    fputc('E', fp);
    fputc('L', fp);
    fputc('L', fp);
    fputc('O', fp);
    fclose(fp);
    return 0;
}
```

<aside> ❓ 해당 소스 파일이 존재하는 폴더에 output.txt 파일이 만들어져있다.

</aside>

------

- 출력 결과

파일 열기에 성공했습니다.

------

### 텍스트 파일 읽기

```c
#include <stdio.h>
 
int main(void)
{
    FILE *fp = NULL;
    int c;
    
    fp = fopen("input.txt","r");
    
    if(fp == NULL)
    {
        printf("파일 열기에 실패했습니다.\\n");
    }
    else
    {
        printf("파일 열기에 성공했습니다.\\n");
    }
    
    while((c = fgetc(fp)) != EOF)
    {
        putchar(c);
    }
    
    fclose(fp);
    return 0;
}
```

------

- 출력 결과

파일 열기에 성공했습니다.

------

```c
#include <stdio.h>
#include <string.h>
 
int main(void)
{
    FILE *fp;
    char fname[256];
    char buffer[256];
    char word[256];
    int line =0;
    
    printf("파일 이름을 입력하세요 :");
    scanf("%s",fname);
    
    printf("탐색할 단어를 입력하세요 :");
    scanf("%s",word);
    
    if((fp =fopen(fname, "r")) == NULL)
    {
        fprintf(stderr, "파일 %s를 열 수 없습니다.\\n", fname);
        return 0;
    }
    
    while(fgets(buffer, 256, fp))
    {
        line++;
        if(strstr(buffer, word))
        {
            printf("라인 %d : 단어 %s이 (가) 발견되었습니다.\\n",line, word);
        }
    }
    
    fclose(fp);
    return 0;
}
```

<aside> ❓ 특정한 메모장이나 단어장 파일에서 어떠한 단어가 몇 번 나오는지 몇 번이나 포함이 되어있는지 찾을 수 있다.

</aside>

------

파일 이름을 입력하세요 : example.txt

탐색할 단어를 입력하세요 : HELLO

라인 1 : 단어 HELLO이(가) 발견되었습니다.

라인 2 : 단어 HELLO이(가) 발견되었습니다.

라인 3 : 단어 HELLO이(가) 발견되었습니다.