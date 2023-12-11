## 구조체

- 객체 지향 프로그래밍에서 말하는 클래스의 모체가 되는 것으로 여러 개의 자료형을 묶어서 새로운 자료형을 만들 수 있는 방법이다.

------

### 학생 정보 구조체

```c
#include <stdio.h>
#include <stdlib.h>

struct student {
    int number;
    char name[10];
    double grade;
};

int main(void)
{
    struct student s;
    s.number = 20200001;
    strcpy(s.name, "홍길동");
    s.grade = 4.5;
    printf("학번 : %d\\n", s.number);
    printf("이름 : %s\\n", s.name);
    printf("학점 : %.1f\\n", s.grade);
    return 0;
}
```

<aside> ❓ 학생의 정보를 더욱 간결하고 명확하게 표현 할 수 있다.

</aside>

------

- 출력 결과

학번 : 20200001 이름 : 홍길동 학점 : 4.5

------

### 학생 정보 구조체 활용

```c
#include <stdio.h>
#include <stdlib.h>

struct student {
    int number;
    char name[10];
    double grade;
};

int main(void)
{
    struct student s;
    
    printf("학번을 입력하세요 : ");
    scanf("%d", &s.number);
    printf("이름을 입력하세요 : ");
    scanf("%s", s.name);
    printf("학점을 입력하세요 : ");
    scanf("%lf", %s.grade);
    
    printf("학번 : %d\\n", s.number);
    printf("이름 : %s\\n", s.name);
    printf("학점 : %.1f\\n", s.grade);
    return 0;
}
```

------

- 출력 결과

학번을 입력하세요 : 2020001

이름을 입력하세요 : 홍길동

학점을 입력하세요 : 4.5

학번 : 20200001 이름 : 홍길동 학점 : 4.5

------

### 두 점 사이의 거리

```c
#include <stdio.h>
#include <math.h>

struct point{
    int x;
    int y;
};

int main(void)
{
    struct point p1, p2;
    int xDiff, yDiff;
    double distance;
    
    printf("1번 점의 좌표를 입력하세요 : ");
    scanf("%d %d", &p1.x, &p1.y);
    
    printf("2번 점의 좌표를 입력하세요 : ");
    scanf("%d %d", &p2.x, &p2.y);
    
    xDiff = p1.x - p2.x;
    yDiff = p1.y - p2.y;
    
    distance = sqrt(xDiff * xDiff + yDiff * yDiff);
    printf("두 점 사이의 거리는 %f입니다.\\n", distance);
    return 0;
}
```

------

- 출력 결과

1번 점의 좌표를 입력하세요 : 1 2

2번 점의 좌표를 입력하세요 : 2 2

두 점 사이의 거리는 1.000000입니다.