# TTL(Time To Live)
- 네트워크 상에서 데이터의 유효 기간을 나타내기 위한 방법입니다.
- 패킷이 무한으로 순환하는 것을 막아주는 역할을 합니다.

## TTL을 설정하는 이유
네트워크에서 패킷이 라우터와 같은 네트워크 장비를 찾아 거치게 되는데 만약 TTL이 설정되어 있지 않고 목적지를 찾지 못한다면 해당 패킷은 네트워크에서 잔류하게 됩니다. 그러므로 TTL을 설정하여 유효 기간을 설정해주고, 목적지를 찾지 못한다면 드랍되게 해주어야 합니다.

TTL을 설정하게 되면 라우터와 같은 네트워크 장비를 거칠 때 TTL의 값이 1씩 감소하게 되고 값이 0이 되면 패킷은 드랍되게 됩니다.

![image](https://github.com/user-attachments/assets/a59c7efa-46f3-41e6-a8b6-a665af03a60c)

## 참고 자료
- https://velog.io/@rkadl9999/TTL%EC%9D%B4-%EB%AD%94%EC%A7%80-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90
- https://velog.io/@numerok/TTL%EC%9D%B4%EB%9E%80
