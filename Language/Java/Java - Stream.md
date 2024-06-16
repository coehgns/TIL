# Stream
- Stream을 사용하여 람다함수형식을 통하여 배열의 원소나 Collection을 가공할 때 깔끔하게 한 번에 가공할 수 있습니다.
	- 가공 방식 : `Map`  `Filter`  `Sorted`
## Stream 생성
-  Collenction -> 스트림
- Collection 인터페이스를 구현한 객체는 .stream()을 통해서 변경 가능합니다.
```java
// List로부터 스트림 생성
List<String> list = Arrays.asList("a", "b", "c");
Stream<String> listStream = list.stream();
```

- 배열 -> 스트림
- stream의 of() 메소드 혹은 Arrays의 stream() 메소드를 통해서 stream으로 변환합니다.
```java
// 배열로 부터 스트림을 생성
Stream<String> stream = Stream.of("a", "b", "c"); 
Stream<String> stream = Stream.of(new String[] {"a", "b", "c"});
Stream<String> stream = Arrays.stream(new String[] {"a", "b", "c"});
Stream<String> stream = Arrays.stream(new String[] {"a", "b", "c"}, 0, 3);
```
# Stream 가공
- stream을 사용하는 이유는 여러가지 데이터가 들어있는 객체의 모든 요소들을 가공 하기 위해서입니다.
## Filtering
- Stream 내에서 특정 조건을 지닌 값들만 필터링하는 메소드입니다.
```java
Stream<Stirng> stream = 
	list.stream()
	.filter(title -> title.contains("code"));
```
- Stream 내에 값들 중 title에 "code"라는 내용이 들어가있는 값만 남깁니다.

## Map
- Stream 내에 값들을 변환하여 새로운 Stream을 만드는 메소드입니다.
- Stream 내에 값들을 특정한 형태로 변환하는데 사용합니다.
```java
String<String> stream =
	title.stream() 
	.map(s -> s.toUpperCase());
```
- Stream 내에 값들의 title을 모두 대문자로 변환합니다.

## Sorted
- Stream 내에 요소들을 정렬하는 메소드입니다.
	- 디폴트 값은 오름차순입니다.
```java
List<String> list = Arrays.asList("apple", "banana", "car");
Stream<String> stream = list.stream()
	.sorted()

Stream<String> stream = list.stream()
	.sorted(Comparator.reverseOrder()) // 내림차순
```

## Distinct
- Stream 내에 중복 값을 제거하는 메소드입니다.
```java
List<String> list = Arrays.asList("apple", "apple", "banana", "car");

Stream<String> stream = list.stream()
	.distinct()  // 중복된 "apple" 제거
```

# Stream 추출
- Stream 내에서 원하는 값을 가져오는 메소드입니다.
```java
long count = IntStream.of(1, 2, 3, 4, 5).count();
long sum = LongStream.of(1, 2, 3, 4, 5).sum();
```
## 참고 자료
- https://codenme.tistory.com/55
