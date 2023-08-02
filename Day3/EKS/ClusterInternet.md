> **EKS cluster가 인터넷 엑세스가 불가능한 환경에서 운영될 수 있는 방법을 정리하고, 실제 해당 방법으로 Cluster를 구성해 보세요.**  

Private 서브넷에 Control plane과 cluster를 배치한 후 Bastion 인스턴스를 통해 kubectl에 접근하여 운영할 수 있을 것입니다.  

또는 VPN을 이용하여 private 서브넷에 접근하여 운영할 수 있을것입니다.