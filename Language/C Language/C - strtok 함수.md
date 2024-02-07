# C - strtok 함수

# strtok

- 문자열을 일정 기준을 정해서 자를 수 있음.
- strtok 헤더파일 : <string.h>
- string을 토큰(token)처럼 조각 내는 함수임.

### strtok 함수 정의

- char* strtok(char* str, char* delimiters);
- char* 타입의 문자열 str을 첫번째 매개변수로 받아서 두번째 매개변수로 들어온 char* 타입의 구분자를 기준으로 문자열을 잘라서 문자열의 포인터를 하나씩 반환하는 함수임.

### 함수 흐름

- 첫번째 인자에는 짜를 문자열, 두번째 인자는 구분할 기준을 집어 넣음.
- strtok이라는 함수는 문장에서 구분자로 들어온 “ “ 공백을 찾음.
- 구분자를 찾게 되면 해당 구분자를 문장의 끝을 알리는 \0으로 바꾸어 줌.
- strtok의 첫번째 반환값은 “Block”이 됨. 이 상태에서 또다시 strtok(NULL, “ “); 함수를 호출하게 되면 이전에 찾은 구분자 뒤에서부터 다시 구분자를 찾게 됨.

```c
char str[] = "Block D Mask.");
char *ptr = strtok(str, " ");
while (ptr != NULL)
{
   printf("%s "), ptr);
   ptr = strtok(NULL, " ");
}
```

## 참고 자료

- https://blockdmask.tistory.com/382