# Java - 계산과 형변환

## 자바에서 계산

1. 같은 타입 끼리의 계산을 같은 타입의 결과를 냅니다.

   - `int`  + `int`는 `int` 를, `double` + `double` 은 `double`의 결과가 나옵니다.

2. 서로 다른 타입의 계산은 큰 범위로 

   자동 형변환

   이 일어납니다.

   - `int` + `long`은 `long` + `long`으로 자동 형변환이 일어납니다.
   - `int` + `double`은 `double` + `double` 로 자동 형변환이 일어납니다.

**Ex**

```java
int div1 = 3 / 2; //int / int
int div1 = 1; //int / int이므로 int타입으로 결과가 나옵니다.

double div2 = 3 / 2; //int / int
double div2 = 1; //int / int이므로 int 타입으로 결과가 나옵니다.
double div2 = (double) 1; //int -> double에 대입해야 합니다. 자동 형변환 발생
double div2 = 1.0; // 1 (int) > 1.0(double)로 형변환 되었다.

double div3 = 3.0 / 2; //double / int
double div3 = 3.0 / (double) 2; //double / int이므로, double / double로 형변환이 발생.
double div3 = 3.0 / 2.0; //double / double -> double이 됩니다.
double div3 = 1,5;

double div4 = (double)3 / 2; // 명시적 형변환을 사용했습니다. (double) int / int
double div4 = (double)3 / (double) 2; double + double로 형변환이 발생했습니다.
double div4 = 3.0 / 2.0; //double / double -> double이 됩니다.
double div4 = 1.5;
```

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194592