### VPC peering
VPC Peering이란 다른 VPC 간에 Private IP로 통신이 가능하도록 연결하는 것을 말합니다.  

다른 리전의 VPC 사이 또는 다른 AWS 계정의 VPC와 Peering도 가능하다.

보통의 VPC 간 통신은 Public IP를 통해 이루어집니다.  
Public IP를 통해 통신을 할 경우 데이터의 안정성에 대한 문제가 발생할 수 있습니다.  

VPC Peering을 사용하면 다른 VPC 간에 Private IP로 통신하기 때문에 데이터의 안정성을 보장받을 수 있습니다.  

쉽게 생각하면 다른 VPC를 서로 연결해서 하나의 네트워크처럼 사용이 가능하도록 합니다.

### VPC Peering의 장점
1. 빠른 네트워크와 트래픽 암호화 및 비용 절감
    *  VPC 피어링은 AWS 백본 네트워크를 경우합니다.  
    따라서 고속 통신이 가능하고 트래픽에 대해 암호화나 전송 비용 절감을 할 수 있습니다.

2. 리전 간 VPC 피어링 지원
    * 몇 개의 중국 리전을 제외하고 전세계 리전 간 VPC 피어링을 지원합니다.

3. 타 계정간 VPC 피어링 지원
    * 동일 계정 내의 VPC 간 피어링 뿐만 아니라 타 게정 사이에도 VPC 피어링을 지원합니다.

### VPC Peering의 제약사항
1. 서로 다른 VPC CIDR(네트워크 대역) 사용 필요
    * 연결한 VPC에 할당된 CIDR가 중복되면 VPC 피어링을 할 수 없습니다.

2. 전이적 피어링을 지원하지 않음
    * VPC 피어링 연결 구성 시 상대방의 VPC의 IP CIDR 대역 외에 다른 대역과 통신이 불가능 합니다.
    * 상대 IP 대역 이외의 다른 대역과 통신이 불가능 하다는 말 입니다.
    * VPC A B Peering / VPC B C Peering이 되어있을때 A C 통신은 Peering을 해주지 않는 이상 불가능 하다는 말입니다.

    
> **두 개의 VPC를 peering으로 연결할 때 다른 VPC의 DNS private zone의 주소를 쿼리 할 수 있는 방법에 대해 조사하고 직접 구성해 보세요.**  

VPC A B를 피어링을 생성해줍니다.  

VPC A / VPC B 의 `DNS 호스트 이름`, `DNS 확인` 옵션을 활성화 해줍니다.

VPC Peering의 DNS 메뉴에서 요청자 VPC와 수락자 VPC 간의 DNS를 프라이빗 IP 주소로 확인하도록 허용하는 옵션을 활성화 해줍니다.