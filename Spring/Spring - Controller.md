# Controller
- 사용자의 요청이 진입하는 지점(entry point)입니다.
- 요청에 따라 어떤 처리를 할지 결정해줍니다.
	- controller는 단지 결정만 해주고 실질적인 처리는 서비스에서 담당합니다.
- 사용자에게 View를 응답으로 보내줍니다.
## controller 사용하는 이유
- 서비스들이 많아지면 하나의 클래스에 몰아 처리하는게 아닌 controller라는 중간 제어자 역할을 하는 것을 만들어서 요청에 대한 controller가 맡아 필요한 로직 처리를 위한 서비스를 호출하게 됩니다.
- controller는 MVC 패턴에 포함되는데 MVC의 역할에 따라 설계하고 코딩하면 개발비용이나 유지보수 비용이 대폭 줄어듭니다.
## 참고 자료
- https://hardlearner.tistory.com/315