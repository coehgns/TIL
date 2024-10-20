# JPQL(Java Persistence Query Language)
- `SQL`을 추상화한 객체지향 쿼리 언어입니다.
- `JPQL`은 객체지향 쿼리 언어이기 때문에 `테이블` 대상이 아닌, `엔티티`를 대상으로 검색합니다.
- `JPQL`의 문법은 `SQL`의 문법과 유사합니다.
- `JPQL`은 `JPA`가 분석한 후 `SQL`로 변환되고, 변환된 `SQL`을 이용하여 `DB`에 접근합니다.
## JPQL의 특징
```sql
select p from Person as p where p.age > 18
```
- `엔티티`와 `속성`은 대소문자로 구분합니다.
	- ex) `엔티티 : Person`, `속성 : age` 
- `테이블` 이름이 아닌 `엔티티` 이름을 사용합니다.
- 별칭(`p`)은 필수적으로 작성해야 합니다.
	- 별칭은 주로 엔티티의 첫 글자를 사용합니다.
- `as`는 생략이 가능합니다.
- `RDB`의 함수를 제공합니다.
## JPQL의 문제점
- `JPQL`은 문자열로 작성되기 때문에 에러가 발생하지 않습니다. 이러한 문제 때문에 에러가 발생하더라도 정상 작동하여 배포할 때에 문제가 될 수 있습니다.
- 동적으로 쿼리를 작성하는 데에 비효율적입니다.
## 참고 자료
- https://ittrue.tistory.com/270
- https://dev-coco.tistory.com/141
- https://ict-nroo.tistory.com/116