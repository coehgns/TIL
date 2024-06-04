# Contoller

- MVC 패턴에서 모델과 뷰의 다리 역할을 합니다.
- FrontController와 Controller로 나눌 수 있습니다.

## FrontController

- 사용자의 모든 요청을 받는 곳 입니다.
- 요청에 따라 View 페이지 또는 Controller를 호출합니다.
- 원하는 작업을 수행한 결과를 가지고 다시 페이지를 이동합니다.

## Controller

- 요청에 따라 어떤 처리를 할지 결정해줍니다.
    - controller는 단지 결정만 해주고 실질적인 처리는 서비스에서 담당합니다.
- `@Controller` 어노테이션을 사용하여 이 클래스가 컨트롤러인지 파악합니다.
- 요청을 처리하는 로직과 필요한 로직을 호출하는 역할을 합니다.
- 사용자에게 View를 응답으로 보내줍니다.

## Controller 클래스 설계

- 클라이언트의 요청과 그 처리 기능에 대해 고민이 담겨 있어야 합니다.

## controller 사용하는 이유

- 서비스들이 많아지면 하나의 클래스에 몰아 처리하는게 아닌 controller라는 중간 제어자 역할을 하는 것을 만들어서 요청에 대한 controller가 맡아 필요한 로직 처리를 위한 서비스를 호출하게 됩니다.
- controller는 MVC 패턴에 포함되는데 MVC의 역할에 따라 설계하고 코딩하면 개발 비용이나 유지 보수 비용이 대폭 줄어듭니다.

## 참고 자료

- [https://hardlearner.tistory.com/315](https://hardlearner.tistory.com/315)
- [https://luanaeun.tistory.com/200](https://luanaeun.tistory.com/200)
