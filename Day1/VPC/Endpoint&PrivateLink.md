### VPC Endpoint
VPC 엔드포인트는 VPC 내부의 Resource들이 VPC 외부의 서비스(S3, Dynamo DB, Cloudwatch 등)에 접근할 때 Internet G/W, NAT G/W 등의 외부 인터넷 전송 서비스를 타지 않고 내부 네트워크를 통해 접근할 수 있도록 지원하는 서비스 입니다.  

인터넷을 통해 VPC 외부의 서비스와 통신시 외부 인터넷에 공개적으로 연결되며 트래픽이 노출됨을 의미합니다.  

만약 내부적으로 은밀하게 처리해야 될 api 호출이라면  인터넷을 통한 통신은 보안상으로 좋지 않은 방법 입니다.  

추가로 VPC 밖에서 들어오는 트래픽에는 과금이 되기 때문에 비용이 늘어납니다.  

쉽게 말해, VPC Endpoint는 AWS의 여러 서비스들과 VPC를 연결시켜주는 중간 매개체로서, AWS에서 VPC 바깥으로 트래픽이 나가지않고 AWS의 여러 서비스들을 사용할수있게 만들어주는 서비스 입니다.

### VPC Endpoint의 이점
1. 보안 측면 강화
2. 비용 절감 효과
3. 서비스 제약
4. VPC 종속
5. 권한 제어

### VPC Endpoint 종류
VPC 엔드포인트는 Interface Endpoint와 라우팅 테이블 기반의 Gateway Endpoint 두가지 종류로 나뉩니다.  

2가지 유형의 다른 부분은 Access 방식 입니다.

Interface Endpoint가 ENI(Elastic Network Interface)를 이용하여 IP가 할당되고 해당 IP로 Access를 하는 방식이면, Gateway Endpoint는 Route Table을 이용하여 Endpoint에 Access한다는 점이 다릅니다.

* Interface Endpoint
    * Private IP를 만들어서 서비스로 연결해줍니다. (SQS, SNS, Kinesis, Sagemaker 등 많은 서비스를 지원합니다.)

* Gateway Endpoint
    * 라우팅 테이블에서 경로의 대상으로 지정하여 사용합니다. (S3, DynamoDB등 일부 서비스만 지원합니다.)

### Priavte Link란
동일한 네트워크대역을 가진 VPC 간의 통신이 불가능하다는 점을 해결할 방법입니다.  

퍼블릭 인터넷에 사용자의 데이터를 노출하지 않고 VPC와 AWS 서비스 및 AWS 파트너가 제공하는 3rd-party 솔루션 간의 프라이빗 한 연결을 제공하는 서비스입니다.  

VPC Endpoint와 함께 활용하여 구축이 가능합니다.