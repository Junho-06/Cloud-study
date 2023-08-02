> **Pod 마다 Security Group을 가질 수 있도록 구성해 보세요.**

1. Sidecar 컨테이너를 활용합니다.  

Pod에 Sidecar 컨테이너를 추가하여 원하는 보안 그룹 설정을 가지고 있는 컨테이너를 함께 실행하여 적용할 수 있습니다.  

이 Sidecar 컨테이너를 통해 Pod에 보안그룹을 적용이 가능합니다.  

2. Amazon VPC CNI plugin for Kubernetes를 사용합니다.  

Amazon VPC CNI plugin for Kubernetes 를 사용하여 Pod에 security group의 ID를 할당하여 사용이 가능해집니다.