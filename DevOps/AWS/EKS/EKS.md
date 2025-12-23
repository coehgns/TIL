# EKS(Elastic Kubernetes Service)
- EKS는 오픈 소스인 쿠버네티스를 AWS에서 운영할 수 있도록 제공해주는 서비스입니다.
- EKS를 사용하면 기존에 직접 쿠버네티스를 구축하는 과정과 운영의 복잡성을 줄일 수 있습니다.
- 컨트롤 플레인을 직접 구축하지 안혹 쿠버네티스를 손쉽게 사용할 수 있습니다.
# EKS 주요 요소
- EKS의 주요 요소에는 `Cluster`, `Node`, `Pod`가 있습니다.
## 1. Cluster
- 클러스터 내부는 **컨트롤 플레인**과 **데이터 플레인**으로 구성되어있습니다.
	- `컨트롤 플레인`: 클러스터의 전반적인 관리와 제어를 하고, 클러스터 내부에 있는 노드를 관리합니다.
	- `데이터 플레인`: 노드가 배치되는 영역입니다.
## 2. Node
- 컨테이너의 실행 환경을 말합니다.
- EKS에서 노드를 EC2 또는 AWS Fargate를 선택할 수 있습니다.
- `Worker Node`라고도 불립니다.
## 3. Pod
- EKS에서 컨테이너의 실행 단위로, `Node` 위에서 `Pod`가 실행됩니다.
## EKS Auto Scaling
 EKS에는 부하에 따라서 Node나 Pod를 자동으로 스케일링해주는 기능을 제공합니다.
 부하가 증가하면 `Scale Out(리소스 증가)`하고, 부하가 감소하면 `Scale In(리소스 감소)`하여 성능 유지와 비용 측면에서 최적화가 가능합니다.
### 1.  HPA(Horizontal Pod Autoscaler)
- HPA는 CPU와 메모리 사용량 등 매트릭량에 따라서 Pod 수를 수평적으로 증감하는 역할을 합니다.
- CPU, 메모리 사용량 등인 메트릭량을 알기 위해서는 메트릭을 수집하는 `Metrics Server`라는 컴포넌트를 별도로 도입해야 합니다.
### 2. KEDA(Kubernetes Event-Driven Autoscaler)
- KEDA는 기존 메트릭을 수집하여 스케일링하던 HPA를 이벤트 기반의 소스로부터 메트릭 수집을 확장한 스케일링 도구입니다.
### 3. VPA(Vertical Pod Autoscaler)
- Pod의 CPU와 메모리 할당량을 조정하여 Pod의 자원 사용을 최적화합니다.
### 4. CA(Cluster Autoscaler)
- 클러스터에서 자동으로 `Node`의 크기를 동적으로 조정하여 현재 필요 여부에 따라 `Node`를 추가하거나 제거하여 클러스터의 용량을 조절합니다. 이를 통해 클러스터의 성능을 최적화하고 리소스를 효율적으로 사용할 수 있습니다.
- CA는 AWS `ASG`를 사용하여 동작합니다.
### 5. CPA(Cluster Proportional Autoscaler)
- `Node` 수 증가에 비례하여 `Pod` 개수를 관리합니다.
- CPA는 `Metrics Server`를 사용하지 않고 `kubapi server API`를 사용합니다.

## 참고 자료
- https://jibinary.tistory.com/400#google_vignette
- https://junho-foodprints.tistory.com/19
- https://kimalarm.tistory.com/61
- https://kschoi728.tistory.com/100
- https://velog.io/@6ain/AEKS2-5%EC%A3%BC%EC%B0%A8-EKS-Autoscaling-CA-CPA
- https://jibinary.tistory.com/307
- https://ssungz.tistory.com/75
- https://nearhome.tistory.com/128