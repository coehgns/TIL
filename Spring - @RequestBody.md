
# **@RequestBody**

- `클라이언트 → 서버` 요청: @RequestBody
- `서버 → 클라이언트` 응답: @ResponseBody
- json 기반의 HTTP Body를 자바 객체로 변환합니다.

```java
public class Entity{
    private Long id;
    private String name;
    private String address;
}

// API Controller
@PostMapping("/api/post")
public void requestTest(@RequestBody Entity entity) {
    System.out.println("id = " + entity.id);
    System.out.println("name = " + entity.name);
    System.out.println("address = " + entity.address);
}
```

- 내용을 HTTP Body에 담아서 POST 요청을 배내게 될 경우 `@RequestBody`는 본문의 내용을 매핑해서 Entity 객체를 생성합니다.

```java
POST /api/post HTTP/1.1

{
    "id": 1,
    "name": "user1"
}
```

- [entity.id](http://entity.id) == 1
- [entity.name](http://entity.name) = “user1”
- entity.address == null

## 참고 자료

- [](https://velog.io/@nomonday/Spring-RequestBody-ResponseBody-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0)[https://velog.io/@nomonday/Spring-RequestBody-ResponseBody-이해하기](https://velog.io/@nomonday/Spring-RequestBody-ResponseBody-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0)