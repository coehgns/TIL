# Java - 자동 형변환

# 자동 형변환

**Casting1**

```java
//intValue = 10
doubleValue = intValue
doubleValue = (double) intValue // 형 맞추기
doubleValue = (double) 10 // 변수 맞추기
doubleValue - 10.0 // 형 변환
```

- `(double)`과 같이 적어주면 `int` 형이 `double`형으로 형이 변합니다.
- 이렇게 형이 변경되는 것을 형변환이라고 합니다.
- 작은 범위 숫자 타입에서 큰 범위 숫자 타입으로의 대입은 개발자가 직접 형변환을 하지 않아도 됩니다.
- 이런 과정이 자동으로 일어나기 때문에 자동 형변환 또는 묵시적 형변환이라고 합니다.

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194590