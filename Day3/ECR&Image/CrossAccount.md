> **1111 AWS account에 ECR repository 하나를 생성하였고, 2222 AWS account의 EKS에서 해당 이미지를 사용하고자 할 때 어떤 설정을 해야 이미지를 가져갈 수 있는지 정리하고 실제로 구성해 보세요.**  

먼저 다른 계정에게 권한을 부여해주어야 합니다.  

1111 AWS 계정에서 IAM role에서 Another AWS account를 선택하고 2222 AWS의 account ID를 입력하고 ECR 레지스트리에 대한 이미지 읽기 권한을 부여합니다.  

2222 AWS 계정에서도 IAM role에서 Another AWS account를 선택하고 1111 AWS의 account ID를 입력하고 EKS 클러스터 생성 관련 정책을 부여합니다.  

EKS를 구성할때 1111 AWS 계정의 ECR 주소를 사용하면 생성이 가능합니다.