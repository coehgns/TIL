# Layered Architecture
- `Layered Architecture`는 관심사의 분리를 위해 하나의 책임을 담당하는 여러 계층으로 분리 한 아키텍쳐입니다.
## 관심사의 분리가 필요한 이유
한 계층에 여러 관심사 가지고 있을 경우 해당 계층은 응집도가 떨어지고 결합도가 높아질 것입니다. 반면 여러 계층을 중심적으로 계층들에 관심사를 분리하는 경우에는 응집도는 높아지고 결합도가 낮아질 것입니다. 이를 통하여 코드의 재사용성과 유지 보수성을 높일 수 있습니다.

따라서 `Layered Architecture`를 사용하면 재사용성과 유지 보수성을 높일 수 있습니다.
## Layered Architecture의 의존성
- 한 계층의 책임 외에 책임은 모두 하위 계층에 의존하게 됩니다. 이때 하위 계층은 상위 계층에 대한 정보가 없어야 합니다.
- 자신보다 상위 계층이나 인접하지 않은 계층에는 요청하지 못합니다.
![Image](https://github.com/user-attachments/assets/ef46e753-693a-4bdf-be60-3bdfbcf9f861)
위와 같이 사용자의 request와 response를 처리하는 계층인 `Presentation Layer`의 하위 계층은 `Business Layer`입니다. 이 때 `Business Layer`는 `Presentation Layer`의 하위 계층이기 때문에 상위 계층인 `Presentation Layer`의 정보를 모릅니다.
## 참고 자료
- https://ksh-coding.tistory.com/92
- https://xxeol.tistory.com/26