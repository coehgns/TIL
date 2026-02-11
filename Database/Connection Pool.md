# Connection Pool
스프링부트를 통해서 백엔드 애플리케이션을 구축하고 `JDBC`를 통해 `DB`에 연결 후 접근하게 됩니다. 이 때 `Connection` 객체를 생성해서 해당 객체가 `DB`에 연결하여 작업 후 연결을 해제합니다. 이렇게  Pool에 접근할 때 마다 `Connection` 객체를 생성 후 작업하고 연결을 해제하기에는 비효율적이기 때문에 이러한 경우 `Connection Pool`을 사용합니다.

`Connection Pool`은 `WAS`가 실행되면서 `Connection` 객체를 미리 만들어 `Pool`에 저장해두었다가 사용자가 `DB`에 접근할 때 `Pool`에 있는 `Connection`들을 사용 후, 반납하여 다시 `Pool`에 저장하게 됩니다.

<img width="1255" height="648" alt="Image" src="https://github.com/user-attachments/assets/ab0ed0ff-d9d6-4c7c-8408-0786a1610fdf" />

## Connection Pool 동작 원리
1. `Thread`가 필요한 `Connection`을 요청합니다.
2. `Pool`에 유효한 `Connection`이 있다면 스레드에게 반환하고 없다면 `HandOffQueue`를 `Poolling`하면서 다른 `Thread`가 `Connection`을 반환하기를 기다립니다.
3. `Thread`가 `Connection`을 반환하면 반납된 `Connection`에 대해서 `Connection Pool`이 사용 내역을 기록하고 `HandOffQueue`에 반납된 `Connection`을 삽입합니다.
4. `HandOffQueue`를 `Poolling` 하던 `Thread`가 삽입된 `Connection`을 반환 받아 사용하게 됩니다.
##  Connection Pool의 장점
- `DB` 접속을 위한 `Connection` 객체를 미리 만들어 메모리 상에 올려두면 `Connection` 객체 생성, 삭제와 같은 작업이 생략되기 때문에 클라이언트가 빠르게 `DB`에 접근이 가능합니다.
- `DB` 작업이 끝난 후 `Pool`에 반납된 `Connection` 객체가 재사용되기 때문에 객체 비용을 줄일 수 있습니다.
- `Connection Pool`에서 `Connection` 수 제한이 가능하기 때문에 자원 고갈 문제를 방지할 수 있습니다.
- 동시에 여러 작업을 처리할 수 있는 연결을 제공하기 때문에 여러 사용자의 요청이 들어와도 애플리케이션에서 안정적으로 처리 가능합니다.
## 유의사항
많은 양의 `Connection`을 생성할 수 있도록 설정하게 되면 `Connection`도 객체이므로 메모리 차지 비율이 많아져 성능 저하로 문제가 될 수 있습니다.
`WAS`에서 `Connection Pool`의 `Connection` 수를 크게 설정하면 사용자의 대기 시간은 줄어들지만 메모리 사용량이 많아지게 되고, `Connection` 수를 작게 설정하면 메모리 사용량이 낮아지지만 사용자의 대기 시간은 늘어나게 되기 때문에 상황에 알맞게 `Coonection Pool`을 사용해야합니다.
## 참고 자료
- https://steady-coding.tistory.com/564
- https://velog.io/@lilychoi/DB-Connection-Pool-%EC%9D%B4%EB%9E%80