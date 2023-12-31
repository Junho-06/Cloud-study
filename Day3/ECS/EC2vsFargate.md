### EC2의 장점
1. 유연한 환경 제어  

EC2 인스턴스를 직접 관리할 수 있기 때문에 컨테이너 실행 환경을 더욱 유연하게 제어할 수 있습니다.  

2. 높은 컨테이너의 사용자 지정 가능  

EC2 인스턴스에서는 컨테이너가 더 많은 리소스를 사용할 수 있습니다.  

3. 저렴한 가격  

EC2 인스턴스를 사용하면 Fargate보다 일반적으로 저렴한 비용으로 컨테이너 실행이 가능합니다.  

### Fargate의 장점
1. 관리의 간소화  

Fargate를 사용하면 컨테이너를 실행하는 데 필요한 EC2 인스턴스 관리가 필요하지 않으므로 운영 부담이 줄어듭니다.  

컨테이너 인프라의 관리 및 유지 보수를 대신해주기 때문에 개발자는 컨테이너 실행에만 집중할 수 있습니다.  

2. 탄력적인 스케일링  

Fargate는 컨테이너를 실행하는 데에 필요한 인프라를 동적으로 조정하여 스케일링을 간단하게 처리합니다.  

트래픽 증가시 자동으로 컨테이너 인스턴스를 추가하고, 트래픽 감소시 자동으로 축소하여 자원으 효율적인 사용이 가능합니다.  

3. 보안 및 격리  

Fargate는 컨테이너를 각각 독립된 환경에서 실행하므로 컨테이너간의 격리가 보장됩니다.  

이를 통해 보안적으로 더 안전한 컨테이너 실행이 가능합니다.  

4. 초당 컨테이너 과금  

Fargate는 사용한 컨테이너의 리소스 사용량에 대해 초당 과금을 제공합니다.  

필요한 리소스만큼만 지불하므로, 비용관리가 효율적 입니다.


### Fargate의 단점
1. 제한된 커스터마이징  

Fargate는 관리의 간소화를 위해 인프라 관리를 대신해주는 서비스이기 때문에 EC2 인스턴스에서 제공하는 커스터마이징 옵션들이 제한됩니다.  

따라서 특정 커널 또는 OS 설정 변경이 필요한 경우 제한적일 수 있습니다.

2. 네트워크 제약  

Fargate는 네트워크의 완전한 제어를 제공하지 않습니다.  

VPC 기반의 컨테이너 실행 환경을 사용하더라도, 기존의 EC2 인스턴스 기반 컨테이너 실행보다 일부 네트워크 기능들에 대한 접근이 제한될 수 있습니다.

3. 추가 비용  

Fargate는 인프라 관리와 관련된 복잡성을 해소해주는 대신, 더 많은 관리 서비스를 제공하기 때문에 EC2 인스턴스를 사용하는 것보다 더 높은 비용이 발생할 수 있습니다.  

초당 실행에 대한 과금이 발생하며, EC2 인스턴스 기반의 클러스터에 비해 세밀한 비용 최적화가 어려울 수 있습니다.

4. 높은 CPU 요구사항  

Fargate는 컨테이너를 실행하는 데 필요한 최소 CPU 용량을 설정해야 합니다.  

컨테이너가 상대적으로 낮은 CPU 요구사항을 가지고 있을 경우, 낮은 CPU 요구사항을 설정할 수 없어 낭비가 발생할 수 있습니다.