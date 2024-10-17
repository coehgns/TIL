# namespace
- 네임스페이스는 리눅스에서 프로세스를 격리 시킬 수 있는 가상화 기술입니다.
- 하나 이상의 프로세스와 리소스들의 집합으로 구성되어 있습니다.
### namespace의 종류
 **네트워크 네임스페이스(network)** : 프로세스의 `네트워크 환경`을 분리할 수 있는 네임스페이스입니다.
- **PID 네임스페이스(pid)** : 프로세스의 `ID`를 격리할 수 있는 네임스페이스입니다.
- **UTS 네임스페이스(uts)** : `호스트 네임`을 분리해주는 네임스페이스입니다.
- **USER 네임스페이스(user)** : 프로세스별로 `UID`와 `GID`를 격리해주는 네임스페이스입니다.
- **시간 네임스페이스(time)** : `시간`을 격리해주는 네임스페이스입니다.
- **마운트 네임스페이스(mnt)** :  파일 시스템 `mount`와 `unmount`의 `작업 공간`을 격리해주는 네임스페이스입니다.
- **IPC 네임스페이스(ipc)** : 프로세스의 `보안`을 위한 네임스페이스입니다.
## 참고 자료
- https://www.44bits.io/ko/keyword/linux-namespace
- https://jaykos96.tistory.com/31
- https://cwal.tistory.com/14
- https://iamjjanga.tistory.com/54
- https://jstar0525.tistory.com/9
- https://0902.tistory.com/7
