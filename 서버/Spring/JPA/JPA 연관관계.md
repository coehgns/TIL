# 연관관계
## 방향

### 단방향

- A 객체 → B 객체 참조 가능
- B 객체 → A 객체 참조 불가능
- 서로 참조 불가능

### 양방향

- A 객체 → B 객체 참조 가능
- B 객체 → A 객체 참조 가능
- 서로 참조 가능

## 연관관계의 주인

- 두 객체가 양방향 관계를 가질 때 그 관계의 주인을 정해주는 것.
- 외래 키가 있는 곳을 주인으로 지정.
- 연관관계의 주인은 두 객체 사이 → 수정, 삭제, 저장, 조회 가능.
- 주인 X → 조회만 가능.

## @OneToOne

- 1 : 1 관계를 설정하는 어노테이션

## @OneToMany

- 1 : N 관계를 설정하는 어노테이션
- Lazy Fetch가 기본 값.
- 해당 어노테이션이 쓰인 필드는 List, Set, Map으로 표현 가능함.

### option

- targetEntity : List<T> 형태를 List로 사용할 수 있게 해줌.
    
    ```java
    @OneToMany(targetEntity = Post.class)
    private List posts;
    ```
    
- mappedBy : 양방향 매핑에서 연관관계 주인을 지정해줌.
    
    ```java
    @OnetoMany(mappedBy = "대상이 되는 변수명")
    List<Post> posts = new ArrayList<>();
    ```
    
- fetch : 애플리케이션이 DB로부터 데이터를 가져옴.
    
    - Lazy Fetch : 연관관계가 있는 엔티티에 접근할 때 DB에 쿼리를 날려 조회함.(지연 로딩)
        
        ```java
        @ManyToOne(fetch = FetchType.Lazy)
        ```
        
    - Eager Fetch : 엔티티의 조회 여부와 상관없이 쿼리를 날림.(즉시 로딩)
        
        ```java
        @ManyToOne(fetch = FetchType.Eager)
        ```
        
- cascade : 한 Entity가 변화가 생기면 연관되어 있는 Entity에도 변화를 전이시킴.
    
    - @ManyToOne에서도 사용 가능.
    - Transient : 객체를 생성한 뒤 데이터를 주어도 JPA나 hibernate가 모르는 상태.(DB 매핑 X)
    - Persistent : JPA가 관리하는 상태.
    - Detached : JPA가 관리하지 않는 상태.
        - 관리하는 상태로 돌아가려면 Persistent로 돌아가야 함.
    - Removed : JPA가 관리하는 상태.
        - 커밋 발생 → 삭제가 일어남.
    
    ```java
    	@OneToMany(cascade = CascadeType.PERSIST)
    	@OneToMany(cascade = {CascadeType.PERSIST, CascadeType.REMOVE)
    ```
    

## @ManyToOne

- N : 1 관계를 설정하는 어노테이션
- Eager Fetch가 기본 값.
- @JoinColumn : 연관관계에서 외래 키를 매핑하기 위해 사용.
    - 속성
        
        - name : 매핑할 외래 키 이름 지정
        
        ```java
        @ManToOne
        @JoinColumn(name = "외래 키 이름")
        private Line line;
        ```
        

## @ManyToMany

- N : M 관계를 설정하는 어노테이션
- RDB에서 일반적인 방법으로 표현할 수 없어서 중간 테이블이 생김.
    - 이러하여 1 : N 과 N : 1로 나누어 사용하여야 하는데 그렇지 않으면 관리가 힘들어지므로 잘 사용하지 않음.

## 참고 자료

- [https://hstory0208.tistory.com/entry/JPA-연관관계-매핑-주인에-대해서-mappedBy](https://hstory0208.tistory.com/entry/JPA-%EC%97%B0%EA%B4%80%EA%B4%80%EA%B3%84-%EB%A7%A4%ED%95%91-%EC%A3%BC%EC%9D%B8%EC%97%90-%EB%8C%80%ED%95%B4%EC%84%9C-mappedBy)
- [https://jeong-pro.tistory.com/231](https://jeong-pro.tistory.com/231)
- [https://velog.io/@goniieee/JPA-OneToMany-ManyToOne으로-연관관계-관리하기](https://velog.io/@goniieee/JPA-OneToMany-ManyToOne%EC%9C%BC%EB%A1%9C-%EC%97%B0%EA%B4%80%EA%B4%80%EA%B3%84-%EA%B4%80%EB%A6%AC%ED%95%98%EA%B8%B0)
- [https://velog.io/@may_yun/JPA-Fetch-전략](https://velog.io/@may_yun/JPA-Fetch-%EC%A0%84%EB%9E%B5)
- [https://velog.io/@max9106/JPA엔티티-상태-Cascade](https://velog.io/@max9106/JPA%EC%97%94%ED%8B%B0%ED%8B%B0-%EC%83%81%ED%83%9C-Cascade)
- [https://ksh-coding.tistory.com/105](https://ksh-coding.tistory.com/105)