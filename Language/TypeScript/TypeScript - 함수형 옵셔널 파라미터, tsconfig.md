# TypeScript - 함수형 옵셔널 파라미터, tsconfig

------

# 함수형 옵셔녈 파라미터(선택적 파라미터)

```tsx
function log(a:string, b?:string) {

}
log('hello world');
log('hello ts', 'abc');
```

- 함수의 옵셔널 파라미터란 해당 값에 ? 물음표를 넣어주면 파라미터에 속한 인자값과 출력되는 값이 비례하지 않아도 됨.
- log를 두 줄 넣었을 때 첫번째 log는 출력되는 값이 1개 일 때 function log(a:string, b?:string) 여기 b에 물음표가 없으면 첫번째 log에 빨간 에러 표시가 생김.이걸 함수의 옵셔널 파라미터라고 부름.

------

# JSON 파일 생성

```tsx
// tsconfig.json

{
  "compilerOptions": {
    "allowJs":true,
    "checkJS":true,
    "nolmplicitAny":true     // 함수 타입을 any라도 지정해주어라 라는 뜻.
  },
  "include":["./src/**/*"]
}
```

------

## 참고 자료

- https://1eemember.tistory.com/5