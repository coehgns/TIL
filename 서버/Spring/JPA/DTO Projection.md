# DTO Projection
- 데이터베이스에서 필요한 데이터만 조회해서 사용할 수 있는 기법입니다.
## DTO Projection을 사용하는 이유
- 특정 상황에서 필요한 필드만 가져올 수 있으므로 성능 최적화에 도움됩니다.
- API 응답에 필요한 데이터만 조회하기 때문에 응답에 최적화되고, 민감한 정보 노출을 방지합니다.

## QueryDSL에서 DTO Projection 방법

### 1. Projections.fields()
 - `Projections.fields()`는 setter가 없어도 필드명으로 매핑되므로 Dto를 불변 객체로 사용하기에 알맞습니다.
 ```Java
 @Getter
public class ClubDto {
    private final Long clubId;  
	private final String clubName;  
	private final String clubImage;  
	private final String introduction;  
	private final List<Major> majors;
}
 ```

### 2. Projections.bean()
- `Projections.bean()`를 사용하기 위해서는 setter와 기본 생성자가 필요합니다. 하지만 DTO 객체는 불변 객체로 유지하는 것을 지향하기 때문에 해당 projection 방법은 지양합니다.
```Java
@Getter
@Setter
@NoArgsConstructor
public class ClubDto {
    private Long clubId;  
	private String clubName;  
	private String clubImage;  
	private String introduction;  
	private List<Major> majors;
}
```

### 3. Projections.construct()
- `Projections.construct()` 생성자를 사용하여 필드에 매핑하는 방법입니다.
-  매핑할 필드들을 생성자의 파라미터에 추가하여 매핑할 수 있는데 Dto에 모든 필드들을 매핑하므로 `@AllArgsConstructor`를 사용합니다.
- Projection의 순서와 Dto 필드의 매핑 순서가 다르면 Exception이 발생하므로 주의해야합니다. 이러한 이유 때문에 유지보수가 어려워져 해당 방법이 지양됩니다.
```Java
@Getter
@AllArgsConstructor  // 필드의 순서대로 파라미터를 갖는 생성자를 생성합니다.
public class ClubDto {
    private final Long clubId;  
	private final String clubName;  
	private final String clubImage;  
	private final String introduction;  
	private final List<Major> majors;
}
```

### 4. @QueryProjection
- Dto의 `Q-Type`을 만들어 사용하는 방법입니다. Dto 생성자 위에 `@QueryProjection`이라는 어노테이션을 작성하여 생성하고, 이럴 경우 컴파일 시점에서 에러를 잡아낼 수 있다는 장점이 있습니다.
```Java
@Getter
public class ClubDto {
    private final Long clubId;  
	private final String clubName;  
	private final String clubImage;  
	private final String introduction;  
	private final List<Major> majors;
	
	@QueryProjection
	public QueryClubVO(Long clubId, String clubName, String clubImage, String introduction, List<Major> majors) {
	    this.clubId = clubId;
	    this.clubName = clubName;
	    this.clubImage = clubImage;
	    this.introduction = introduction;
	    this.majors = majors;
	}

}
```

## 장점
- 필요한 데이터만 조회하므로 성능이 최적화됩니다.
- 연관 엔티티를 직접 사용하지 않기 때문에 N+1 문제를 회피할 수 있습니다.
- 명확환 데이터 구조를 정의하기 때문에 가독성이 향상됩니다.
## 단점
- DTO 클래스를 추가적으로 정의해야합니다.
- 복잡한 관계를 표현하는데 한계가 있습니다.
## 참고 자료
- https://velog.io/@bagt/QueryDsl-DTO-Projection
- https://velog.io/@lolu1032/DTO-Projection%EB%A5%BC-%EC%99%9C-%EC%93%B0%EB%8A%94%EA%B1%B8%EA%B9%8C
- https://che01.tistory.com/85
- https://j-dong.tistory.com/11