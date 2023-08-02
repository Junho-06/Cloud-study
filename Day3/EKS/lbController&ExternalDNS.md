### AWS LB Controller란
쿠버네티스가 외부의 트래픽을 받기 위해 Ingress 리소스를 생성할 경우 자동으로 AWS Load Balancer Controller가 트리거하여 ingress.yaml 템플릿에 명시된대로 로드밸런서를 생성해주는 컨트롤러 입니다.  

즉, Cluster에 Ingress 자원이 생성될 때 ALB 및 필요한 자원이 생성되도록 Trigger하는 컨트롤러 입니다.  

Ingress 자원들은 ALB를 구성하여 HTTP 혹은 HTTPS 트래픽을 클러스터 내 Pod로 라우팅하게 됩니다.  

AWS LB Controller에서 지원하는 Traffic Mode는 아래 2가지 입니다. 

1. Instance  

클러스터 내 노드를 ALB의 대상으로 등록합니다.  

ALB에 도달하는 트래픽은 NodePort로 라우팅된 다음 파드로 프록시 됩니다.  

2. IP  

Pod를 IP 대상으로 등록합니다.  

ALB에 도달하는 트래픽은 파드로 직접 라우팅되며 해당 트래픽 모드를 사용하기 위해선 ingress.yaml 파일에 Annotation을 사용하여 명시적으로 지정해야 합니다.

### External DNS란
External DNS는 Kubernetes dns와 상반되는 개념으로 내부 도메인서버가 아닌 Public한 도메인서버를 사용하여 쿠버네티스의 리소스를 쿼리할 수 있게 해주는 오픈소스 솔루션 입니다.  

External DNS를 사용하면 public 도메인 서버가 무엇이든 상관없이 쿠버네티스 리소스를 통해서 DNS레코드를 동적으로 관리 할 수 있습니다.