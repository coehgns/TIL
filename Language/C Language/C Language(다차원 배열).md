## 다차원 배열

- 배열이 배열의 원소로 들어가는 구조를 말한다.

### 구구단을 이용하여 이차원 배열을 출력하는 프로그램

```c
#include <stdio.h>

int main(void)
{
    int i,j;
    int gugudan[10][10];
    for(i=1; i<=9;i++)
    {
        printf("\\n[ %d단 ]\\n\\n",i);
        for(j=1; j<=9;j++)
        {
            gugudan[i][j]=i*j;
            printf("%d X %d =%d\\n",i,j,gugudan[i][j]);
        }
    }
    return 0;
}
```

------

- 출력 결과

[ 1단 ]    ~~~[ 9단]

1 X 1 =1 1 X 2 =2 1 X 3 =3 1 X 4 =4 1 X 5 =5 1 X 6 =6 1 X 7 =7 1 X 8 =8 1 X 9 =9

------

학생 점수의 총 합 계산 프로그램

```c
#include <stdio.h>

int main(void)
{
    int score[5][2];
    int total[2] = { 0, };
    int i;
    
    for(i=0;i<5;i++)
    {
        printf("%d번 학생의 수학, 영어 점수 :",i+1);
        scanf("%d %d", &score[i][0], &score [i][1]);
    }
    for(i=0;i<5;i++)
    {
        total[0] += score[i][0];
        total[1] += score[i][1];
    }
    printf("\\n\\n5명의 수학 점수 합계:%d\\n",total[0]);
    printf("5명의 영어 점수 합계 %d\\n",total[1]);
    return 0;
```

------

- 출력 결과

1번 학생의 수학 점수, 영어 점수: 30 50

2번 학생의 수학 점수, 영어 점수: 40 60

3번 학생의 수학 점수, 영어 점수: 20 10

4번 학생의 수학 점수, 영어 점수: 45 60

5번 학생의 수학 점수, 영어 점수: 70 80

5명의 수학 점수 합계:205

5명의 영어 점수 합계:260