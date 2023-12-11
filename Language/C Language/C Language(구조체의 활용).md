# 구조체의 활용

### 사각형의 넓이와 둘레를 구하는 프로그램

```c
#include <stdio.h>
#include <math.h>

struct point{
    int x;
    int y;
};

struct rect {
    struct point p1;
    struct point p2;
};

int main(void)
{
    struct rect r;
    int w, h, area, peri;
    
    printf("왼쪽 상단의 좌표를 입력하세요 : ");
    scanf("%d %d", &r.p1.x, &r.p1.y);
    
    printf("오른쪽 하단의 좌표를 입력하세요 : ");
    scanf("%d %d ", &r.p2.x, &r.p2.y);
    
    w = abs(r.p2.x - r.p1.x);
    h = abs(r.p2.y - r.p1.y);
    area = w * h;
    peri = 2 * w + 2 * h;
    
    printf("사각형의 넓이는 %d이고, 둘레는 %d 입니다.", area, peri);
    return 0;
}
```

------

- 출력 결과

왼쪽 상단의 좌표를 입력하세요 : -10 10

오른쪽 하단의 좌표를 입력하세요 : 5 3

사각형의 넓이는 105이고, 둘레는 44 입니다.

------

### 구조체의 비교

```c
#include <stdio.h>

struct point{
    int x;
    int y;
};

void comparePoint (struct point p1, struct point p2){
    if((p1.x == p2.x) && (p1.y == p2.y))
    {
        printf("p1과 p2가 같습니다.");
    }
}
int main(void)
{
    struct point p1;
    struct point p2;
    
    p1.x = 30;
    p1.y = 10;
    
    p2.x = 30;
    p2.y = 10;
    
    /*if(p1 == p2)
    {
        printf("p1과 p2가 같습니다.");
    }*/
    comparePoint(p1,p2);
   
    
    return 0;
}
```

------

- 출력 결과

p1과 p2가 같습니다.

------

### 구조체의 배열

```c
#include <stdio.h>
#define SIZE 3

struct student {
    int number;
    char name[20];
    double grade; //GPA -> 학점
};
int main(void)
{
    struct student list[SIZE];
    int i;
    
    for(i = 0; i < SIZE; i++)
    {
        printf("학번을 입력하세요 :");
        scanf("%d", &list[i].number);
        printf("이름을 입력하세요 :");
        scanf("%s", list[i].name);
        printf("학점을 입력하세요 :");
        scanf("%lf", &list[i].grade);
    }
    
    for(i = 0; i < SIZE; i++)
    {
        printf("학번 : %d, 이름 : %s, 학점 : %.1f", list[i].number,list[i].name,list[i].grade);
    }
    return 0;
}
```

------

- 출력 결과

학번을 입력하세요 :1

이름을 입력하세요 :홍길동

학점을 입력하세요 :3.4

학번을 입력하세요 :2

이름을 입력하세요 :이순신

학점을 입력하세요 :4.1

학번을 입력하세요 :3

이름을 입력하세요 :김태영

학점을 입력하세요 :2.4

학번 : 1, 이름 : 홍길동, 학점 : 3.4

학번 : 2, 이름 : 이순신, 학점 : 4.1

학번 : 3, 이름 : 김태영, 학점 : 2.4